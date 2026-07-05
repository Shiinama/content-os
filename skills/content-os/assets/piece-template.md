---
id: {kebab-case-slug}
created: {YYYY-MM-DD HH:MM}
updated: {YYYY-MM-DD HH:MM}
status: drafting
ideas: [{source idea card ids}]
template: {text template card id, or empty if written bare}
visual_template: {image-prompt card id, or empty; use a {platform: id} map when platforms diverge}
platforms:
  {platform}: draft        # draft | final | published <url>
visuals:
  {platform}: pending      # none | pending | generated | approved
---
<!-- generated images live in assets/ as <platform>-cover.png, <platform>-slide-NN.png, <platform>-inline-NN.png -->

## Production Notes
- [{YYYY-MM-DD HH:MM}] {angle chosen, what was cut, decisions worth remembering; append-only}

## Performance
<!-- appended after publishing, one timestamped snapshot per report: - [date] platform: metrics as given. Never overwrite old snapshots; the trend is the point. -->
