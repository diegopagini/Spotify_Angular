### ng-template-context

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
