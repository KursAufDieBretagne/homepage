---
title: "Kontakt"
date: 2026-03-06
draft: false
translationKey: "kontakt"
---
<form action="https://formspree.io/f/mwvrkran" method="POST" class="contact-form">
  <input type="text" name="_gotcha" style="display:none">

  <label style="display:block; margin-top: 10px;">
    Ihr Name:
    <input type="text" name="name" required style="width: 100%; padding: 8px; margin-top: 5px;">
  </label>
  
  <label style="display:block; margin-top: 10px;">
    Ihre E-Mail:
    <input type="email" name="email" required style="width: 100%; padding: 8px; margin-top: 5px;">
  </label>
  
  <label style="display:block; margin-top: 10px;">
    Ihre Nachricht:
    <textarea name="message" rows="5" required style="width: 100%; padding: 8px; margin-top: 5px;"></textarea>
  </label>

  <label style="display:block; margin-top: 15px; font-size: 0.9em;">
    <input type="checkbox" name="privacy_accepted" required style="margin-right: 5px;">
    Ich habe die <a href="/datenschutz/">Datenschutzerklärung</a> gelesen und erkläre mich mit der Verarbeitung meiner Daten einverstanden. *
  </label>
  
  <button type="submit" style="margin-top: 15px; padding: 10px 20px; background-color: #003b6f; color: white; border: none; cursor: pointer;">
    Nachricht senden
  </button>
</form>
