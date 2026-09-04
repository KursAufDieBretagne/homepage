---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: false
translationKey: "{{ .Name }}"
---

Bilder, Video-Impressionen & Social Media zu diesem Ereignis.

{{< gallery cols="2" >}}

{{< youtube id="YOUTUBE_VIDEO_ID" title="Video Titel" caption="Kurze Beschreibung des Videos" >}}

{{< photo src="/img/impressionen/beispiel.jpg" title="Foto Titel" caption="Kurze Beschreibung des Fotos" >}}

{{< instagram url="https://www.instagram.com/p/INSTAGRAM_POST_ID/" title="Instagram Beitrag" caption="Beschreibung des Instagram-Posts" mode="card" image="/img/impressionen/beispiel.jpg" >}}

{{< /gallery >}}
