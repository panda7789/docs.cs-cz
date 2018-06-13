---
title: Přehled třídy SoundPlayer
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 31ce87303b7b96cfd14d4daf07fd21c9de91a548
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535961"
---
# <a name="soundplayer-class-overview"></a><span data-ttu-id="2f027-102">Přehled třídy SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="2f027-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="2f027-103"><xref:System.Media.SoundPlayer> Vám umožňuje snadno zahrnout zvuky ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="2f027-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="2f027-104"><xref:System.Media.SoundPlayer> Třídy můžete přehrát zvukové soubory ve formátu WAV, z prostředku nebo z umístění UNC nebo HTTP.</span><span class="sxs-lookup"><span data-stu-id="2f027-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="2f027-105">Kromě toho <xref:System.Media.SoundPlayer> vám umožňuje načíst nebo přehrání zvuků asynchronně.</span><span class="sxs-lookup"><span data-stu-id="2f027-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="2f027-106">Můžete také <xref:System.Media.SystemSounds> třída přehrávání běžné systémové zvuky, včetně zvukový signál.</span><span class="sxs-lookup"><span data-stu-id="2f027-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="2f027-107">Běžně používané vlastnosti, metod a události</span><span class="sxs-lookup"><span data-stu-id="2f027-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="2f027-108">Název</span><span class="sxs-lookup"><span data-stu-id="2f027-108">Name</span></span>|<span data-ttu-id="2f027-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2f027-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="2f027-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2f027-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> property</span></span>|<span data-ttu-id="2f027-111">Cesta k souboru nebo webovou adresu zvuku.</span><span class="sxs-lookup"><span data-stu-id="2f027-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="2f027-112">Přípustné hodnoty může být cesta UNC nebo HTTP.</span><span class="sxs-lookup"><span data-stu-id="2f027-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<span data-ttu-id="2f027-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2f027-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> property</span></span>|<span data-ttu-id="2f027-114">Počet milisekund, po které vašeho programu bude čekat na načítání zvuku dříve, než se vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="2f027-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="2f027-115">Výchozí hodnota je 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="2f027-115">The default is 10 seconds.</span></span>|  
|<span data-ttu-id="2f027-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2f027-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> property</span></span>|<span data-ttu-id="2f027-117">Logická hodnota, která určuje, zda se dokončil načítání.</span><span class="sxs-lookup"><span data-stu-id="2f027-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<span data-ttu-id="2f027-118"><xref:System.Media.SoundPlayer.Load%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="2f027-118"><xref:System.Media.SoundPlayer.Load%2A> method</span></span>|<span data-ttu-id="2f027-119">Načte zvuk synchronně.</span><span class="sxs-lookup"><span data-stu-id="2f027-119">Loads a sound synchronously.</span></span>|  
|<span data-ttu-id="2f027-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="2f027-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> method</span></span>|<span data-ttu-id="2f027-121">Zahájí asynchronní načítání zvuku.</span><span class="sxs-lookup"><span data-stu-id="2f027-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="2f027-122">Po dokončení načítání vyvolá <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> událostí.</span><span class="sxs-lookup"><span data-stu-id="2f027-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<span data-ttu-id="2f027-123"><xref:System.Media.SoundPlayer.Play%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="2f027-123"><xref:System.Media.SoundPlayer.Play%2A> method</span></span>|<span data-ttu-id="2f027-124">Hraje zvuk zadaný v <xref:System.Media.SoundPlayer.SoundLocation%2A> nebo <xref:System.Media.SoundPlayer.Stream%2A> vlastnost v nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="2f027-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<span data-ttu-id="2f027-125"><xref:System.Media.SoundPlayer.PlaySync%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="2f027-125"><xref:System.Media.SoundPlayer.PlaySync%2A> method</span></span>|<span data-ttu-id="2f027-126">Hraje zvuk zadaný v <xref:System.Media.SoundPlayer.SoundLocation%2A> nebo <xref:System.Media.SoundPlayer.Stream%2A> vlastnost v aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="2f027-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<span data-ttu-id="2f027-127"><xref:System.Media.SoundPlayer.Stop%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="2f027-127"><xref:System.Media.SoundPlayer.Stop%2A> method</span></span>|<span data-ttu-id="2f027-128">Ukončí všechny aktuálně přehrávání zvuku.</span><span class="sxs-lookup"><span data-stu-id="2f027-128">Stops any sound currently playing.</span></span>|  
|<span data-ttu-id="2f027-129"><xref:System.Media.SoundPlayer.LoadCompleted> Události</span><span class="sxs-lookup"><span data-stu-id="2f027-129"><xref:System.Media.SoundPlayer.LoadCompleted> event</span></span>|<span data-ttu-id="2f027-130">Vyvolána po dojde k pokusu o načtení zvuku.</span><span class="sxs-lookup"><span data-stu-id="2f027-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f027-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f027-131">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>
