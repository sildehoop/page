---
name: chips
internal: true
code: |-
  chips:
    tap_action:
      action: more-info
    show_icon: false
    show_label: true
    show_name: false
    show_state: false
    styles:
      label:
        - justify-self: center
        - padding: 0px 6px
        - font-weight: bold
        - font-size: 14px
      img_cell:
        - width: 24px
      grid:
        - grid-template-areas: '"l"'
      card:
        - border-radius: 18px
        - box-shadow: var(--box-shadow)
        - height: 36px
        - width: auto
        - padding-left: 6px
        - padding-right: 6px
    size: 80%
---