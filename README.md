## ng-template-context

```html
<ng-container
  *ngTemplateOutlet="coverSection; context: { track: track }"
></ng-container>
      
<ng-template #coverSection let-track="track">
  <div class="cover-section">
    <img
      appImgBroken
      class="cover-track"
      [src]="track.cover"
      [alt]="track.name"
    />
    <div class="cover-info">
      <div class="name-track">{{ track.name }}</div>
      <div class="name-track-details">{{ track.artist.name }}</div>
    </div>
  </div>
</ng-template>
```

---

## directive 

### img-broken.directive.ts
```typescript
import { Directive, ElementRef, HostListener, Input } from '@angular/core';

@Directive({
  selector: 'img[appImgBroken]',
})
export class ImgBrokenDirective {
  @Input() customImg: string = '';
  @HostListener('error') handleError(): void {
    const elNative = this.elHost.nativeElement;
    elNative.src = this.customImg;
  }

  constructor(private elHost: ElementRef) {}
}
```

### card-player.component.html
```html
<img
  appImgBroken
  [customImg]="
    'https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Angular_full_color_logo.svg/2048px-Angular_full_color_logo.svg.png'
  "
  [src]="track.cover"
  alt=""
  class="cover"
/>
```
