---
title: Contact Form

form:
    name: contact

    fields:
        - name: name
          label: Name
          placeholder: Enter your name...
          autofocus: on
          autocomplete: on
          type: text
          validate:
            required: true

        - name: email
          label: Email
          placeholder: Enter your email address...
          type: email
          validate:
            required: true

        - name: message
          label: Message
          placeholder: Enter your message...
          type: textarea
          validate:
            required: true

        - name: g-recaptcha-response
          label: Captcha
          type: captcha
          recaptcha_site_key: 6LffVRsUAAAAAHZ_ka4OsTdpP6tjT_jtN_evDH9d
          recaptcha_not_validated: 'Captcha not valid!'
          validate:
            required: true

    buttons:
        - type: submit
          value: Submit
          classes: btn btn-color
        - type: reset
          value: Reset
          classes: btn btn-color

    process:
        - captcha:
            recaptcha_secret: 6LffVRsUAAAAAA8Lz9KuL5tyxNxGGERqeU6SDRcN
        - email:
            subject: "[Site Contact Form] {{ form.value.name|e }}"
            body: "{% include 'forms/data.html.twig' %}"
        - save:
            fileprefix: contact-
            dateformat: Ymd-His-u
            extension: txt
            body: "{% include 'forms/data.txt.twig' %}"
        - message: Thank you for getting in touch!
        - display: thankyou
---

