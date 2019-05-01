---
title: Přehled třídy SoundPlayer
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 3ff23cbfa78b803d4526e7a7c389fd5d458a967c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972000"
---
# <a name="soundplayer-class-overview"></a>Přehled třídy SoundPlayer
<xref:System.Media.SoundPlayer> Třída umožňuje snadno zahrnout zvuky ve svých aplikacích.  
  
 <xref:System.Media.SoundPlayer> Třídy můžete přehrávat zvukové soubory ve formátu WAV, z prostředku nebo z umístění UNC nebo HTTP. Kromě toho <xref:System.Media.SoundPlayer> třída umožňuje načíst nebo přehrát zvuky asynchronně.  
  
 Můžete také použít <xref:System.Media.SystemSounds> třídy k přehrání běžné systémové zvuky, včetně zvukový signál.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Běžně používané vlastnosti, metody a události  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A> Vlastnost|Cesta k souboru nebo webovou adresu zvuku. Přípustné hodnoty může být název UNC nebo HTTP.|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A> Vlastnost|Počet milisekund, po které váš program bude čekat na načítání zvuku dříve, než dojde k výjimce. Výchozí hodnota je 10 sekund.|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A> Vlastnost|Logická hodnota označující, zda zvuk dokončení načítání.|  
|<xref:System.Media.SoundPlayer.Load%2A> – Metoda|Načte zvuk synchronně.|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A> – Metoda|Zahájí asynchronní načítání zvuku. Po dokončení načítání se vyvolá <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> událostí.|  
|<xref:System.Media.SoundPlayer.Play%2A> – Metoda|Přehraje zvuk podle <xref:System.Media.SoundPlayer.SoundLocation%2A> nebo <xref:System.Media.SoundPlayer.Stream%2A> vlastnost v nové vlákno.|  
|<xref:System.Media.SoundPlayer.PlaySync%2A> – Metoda|Přehraje zvuk podle <xref:System.Media.SoundPlayer.SoundLocation%2A> nebo <xref:System.Media.SoundPlayer.Stream%2A> vlastnost v aktuálním vlákně.|  
|<xref:System.Media.SoundPlayer.Stop%2A> – Metoda|Zastaví všechny aktuálně přehrávání zvuku.|  
|<xref:System.Media.SoundPlayer.LoadCompleted> Události|Je aktivována po pokusu o načtení zvuk.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
