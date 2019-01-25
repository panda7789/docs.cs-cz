---
title: Přehled třídy SoundPlayer
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 041e7d0170bc98797278e209fd86cff0f82db9fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690683"
---
# <a name="soundplayer-class-overview"></a><span data-ttu-id="08fa2-102">Přehled třídy SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="08fa2-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="08fa2-103"><xref:System.Media.SoundPlayer> Třída umožňuje snadno zahrnout zvuky ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="08fa2-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="08fa2-104"><xref:System.Media.SoundPlayer> Třídy můžete přehrávat zvukové soubory ve formátu WAV, z prostředku nebo z umístění UNC nebo HTTP.</span><span class="sxs-lookup"><span data-stu-id="08fa2-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="08fa2-105">Kromě toho <xref:System.Media.SoundPlayer> třída umožňuje načíst nebo přehrát zvuky asynchronně.</span><span class="sxs-lookup"><span data-stu-id="08fa2-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="08fa2-106">Můžete také použít <xref:System.Media.SystemSounds> třídy k přehrání běžné systémové zvuky, včetně zvukový signál.</span><span class="sxs-lookup"><span data-stu-id="08fa2-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="08fa2-107">Běžně používané vlastnosti, metody a události</span><span class="sxs-lookup"><span data-stu-id="08fa2-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="08fa2-108">Název</span><span class="sxs-lookup"><span data-stu-id="08fa2-108">Name</span></span>|<span data-ttu-id="08fa2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="08fa2-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="08fa2-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="08fa2-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> property</span></span>|<span data-ttu-id="08fa2-111">Cesta k souboru nebo webovou adresu zvuku.</span><span class="sxs-lookup"><span data-stu-id="08fa2-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="08fa2-112">Přípustné hodnoty může být název UNC nebo HTTP.</span><span class="sxs-lookup"><span data-stu-id="08fa2-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<span data-ttu-id="08fa2-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="08fa2-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> property</span></span>|<span data-ttu-id="08fa2-114">Počet milisekund, po které váš program bude čekat na načítání zvuku dříve, než dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="08fa2-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="08fa2-115">Výchozí hodnota je 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="08fa2-115">The default is 10 seconds.</span></span>|  
|<span data-ttu-id="08fa2-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="08fa2-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> property</span></span>|<span data-ttu-id="08fa2-117">Logická hodnota označující, zda zvuk dokončení načítání.</span><span class="sxs-lookup"><span data-stu-id="08fa2-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<span data-ttu-id="08fa2-118"><xref:System.Media.SoundPlayer.Load%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="08fa2-118"><xref:System.Media.SoundPlayer.Load%2A> method</span></span>|<span data-ttu-id="08fa2-119">Načte zvuk synchronně.</span><span class="sxs-lookup"><span data-stu-id="08fa2-119">Loads a sound synchronously.</span></span>|  
|<span data-ttu-id="08fa2-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="08fa2-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> method</span></span>|<span data-ttu-id="08fa2-121">Zahájí asynchronní načítání zvuku.</span><span class="sxs-lookup"><span data-stu-id="08fa2-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="08fa2-122">Po dokončení načítání se vyvolá <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> událostí.</span><span class="sxs-lookup"><span data-stu-id="08fa2-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<span data-ttu-id="08fa2-123"><xref:System.Media.SoundPlayer.Play%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="08fa2-123"><xref:System.Media.SoundPlayer.Play%2A> method</span></span>|<span data-ttu-id="08fa2-124">Přehraje zvuk podle <xref:System.Media.SoundPlayer.SoundLocation%2A> nebo <xref:System.Media.SoundPlayer.Stream%2A> vlastnost v nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="08fa2-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<span data-ttu-id="08fa2-125"><xref:System.Media.SoundPlayer.PlaySync%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="08fa2-125"><xref:System.Media.SoundPlayer.PlaySync%2A> method</span></span>|<span data-ttu-id="08fa2-126">Přehraje zvuk podle <xref:System.Media.SoundPlayer.SoundLocation%2A> nebo <xref:System.Media.SoundPlayer.Stream%2A> vlastnost v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="08fa2-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<span data-ttu-id="08fa2-127"><xref:System.Media.SoundPlayer.Stop%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="08fa2-127"><xref:System.Media.SoundPlayer.Stop%2A> method</span></span>|<span data-ttu-id="08fa2-128">Zastaví všechny aktuálně přehrávání zvuku.</span><span class="sxs-lookup"><span data-stu-id="08fa2-128">Stops any sound currently playing.</span></span>|  
|<span data-ttu-id="08fa2-129"><xref:System.Media.SoundPlayer.LoadCompleted> Události</span><span class="sxs-lookup"><span data-stu-id="08fa2-129"><xref:System.Media.SoundPlayer.LoadCompleted> event</span></span>|<span data-ttu-id="08fa2-130">Je aktivována po pokusu o načtení zvuk.</span><span class="sxs-lookup"><span data-stu-id="08fa2-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08fa2-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08fa2-131">See also</span></span>
- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
