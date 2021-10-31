---
title: Light Slider Card (collapse)
name: card_light_slider_collapse
category: card
explanation: "The `light-slider-card (collapse)` is an enhanced version of the `light-slider-card`, that only shows the slider, if the light is on. In the picture on the right, the 'off'-state is like row Nr1, the 'on'-state like row Nr2"
image_path: "/assets/images/card_light_combi.png"
internal: false
generator_install: true
generator_example: true
generator_button: true
variables:
  - name: entity
    type: entry
    example: light.my_livingroom_light
    required: true 
    explanation: ""
  - name: ulm_card_light_slider_collapse_name
    type: variable
    example: Livingroom Light
    required: false 
    explanation: "If you want to set a specific name, eg. because your friendly name is too long for the card, this is the place to fill it in. If this is not set, the friendly name will be used."
yaml: |-
  - type: 'custom:button-card'
    template: card_light_slider_collapse
    variables:
      ulm_card_light_slider_collapse_name: Livingroom Light
    entity: light.my_livingroom_light
ui: |-
  type: 'custom:button-card'
  template: card_light_slider_collapse
  variables:
    ulm_card_light_slider_collapse_name: Livingroom Light
  entity: light.my_livingroom_light
code: |-
  card_light_slider_collapse:
    variables:
      ulm_card_light_slider_collapse_name: "[[[ return entity.attributes.friendly_name ]]]"
    show_icon: false
    show_name: false
    show_label: false
    state:
      - operator: template
        value: "[[[ return entity.state == 'on' ]]]"
        styles:
          grid:
            - row-gap: 12px
          card:
            - background-color: 'rgba(var(--color-background-yellow),var(--opacity-bg))'
    styles:
      grid:
        - grid-template-areas: '"item1" "item2"'
        - grid-template-columns: 1fr
        - grid-template-rows: min-content min-content
      card:
        - border-radius: var(--border-radius)
        - box-shadow: var(--box-shadow)
        - padding: 12px
    custom_fields:
      item1:
        card:
          type: 'custom:button-card'
          template:
            - icon_info
            - light
          entity: "[[[ return entity.entity_id ]]]"
          name: "[[[ return variables.ulm_card_light_slider_name ]]]"
          styles:
            card:
              - box-shadow: none
              - border-radius: var(--border-radius) var(--border-radius) 0px 0px
              - padding: 0px
      item2:
        card:
          type: conditional
          conditions:
            - entity: "[[[ return entity.entity_id ]]]"
              state: 'on'
          card:
            type: 'custom:my-slider'
            entity: '[[[ return entity.entity_id ]]]'
            radius: 14px
            height: 42px
            mainSliderColor: rgba(var(--color-yellow),1)
            secondarySliderColor: rgba(var(--color-yellow),0.2)
            mainSliderColorOff: rgba(var(--color-theme),0.05)
            secondarySliderColorOff: rgba(var(--color-theme),0.05)
            thumbHorizontalPadding: '0px'
            thumbVerticalPadding: '0px'   
            thumbWidth: 0px
            card_mod:
            style: |
              ha-card {
                border-radius: 14px;
                box-shadow: none;
              }
---