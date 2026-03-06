---
title: "Contact"
date: 2026-03-06T18:00:00
draft: false
translationKey: "kontakt"
---
<form action="https://form.taxi/s/dp02dale" method="POST" class="contact-form">
  <input type="text" name="_gotcha" style="display:none">

  <label style="display:block; margin-top: 10px;">
    Votre nom:
    <input type="text" name="name" required style="width: 100%; padding: 8px; margin-top: 5px;">
  </label>
  
  <label style="display:block; margin-top: 10px;">
    Votre e-mail:
    <input type="email" name="email" required style="width: 100%; padding: 8px; margin-top: 5px;">
  </label>
  
  <label style="display:block; margin-top: 10px;">
    Votre message :
    <textarea name="message" rows="5" required style="width: 100%; padding: 8px; margin-top: 5px;"></textarea>
  </label>

  <label style="display:block; margin-top: 15px; font-size: 0.9em;">
    <input type="checkbox" name="privacy_accepted" required style="margin-right: 5px;">
    J'ai lu la <a href="/datenschutz/">déclaration de confidentialité</a> et j'accepte le traitement de mes données. *
  </label>
  
  <button type="submit" style="margin-top: 15px; padding: 10px 20px; background-color: #003b6f; color: white; border: none; cursor: pointer;">
    Envoyer message
  </button>
</form>
