---
title: Přehled třídy SoundPlayer
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 3ff23cbfa78b803d4526e7a7c389fd5d458a967c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195004"
---
# <a name="soundplayer-class-overview"></a><span data-ttu-id="713f5-102">Přehled třídy SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="713f5-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="713f5-103"><xref:System.Media.SoundPlayer> Třída umožňuje snadno zahrnout zvuky ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="713f5-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="713f5-104"><xref:System.Media.SoundPlayer> Třídy můžete přehrávat zvukové soubory ve formátu WAV, z prostředku nebo z umístění UNC nebo HTTP.</span><span class="sxs-lookup"><span data-stu-id="713f5-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="713f5-105">Kromě toho <xref:System.Media.SoundPlayer> třída umožňuje načíst nebo přehrát zvuky asynchronně.</span><span class="sxs-lookup"><span data-stu-id="713f5-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="713f5-106">Můžete také použít <xref:System.Media.SystemSounds> třídy k přehrání běžné systémové zvuky, včetně zvukový signál.</span><span class="sxs-lookup"><span data-stu-id="713f5-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="713f5-107">Běžně používané vlastnosti, metody a události</span><span class="sxs-lookup"><span data-stu-id="713f5-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="713f5-108">Name</span><span class="sxs-lookup"><span data-stu-id="713f5-108">Name</span></span>|<span data-ttu-id="713f5-109">Popis</span><span class="sxs-lookup"><span data-stu-id="713f5-109">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A> <span data-ttu-id="713f5-110">property</span><span class="sxs-lookup"><span data-stu-id="713f5-110">property</span></span>|<span data-ttu-id="713f5-111">Cesta k souboru nebo webovou adresu zvuku.</span><span class="sxs-lookup"><span data-stu-id="713f5-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="713f5-112">Přípustné hodnoty může být název UNC nebo HTTP.</span><span class="sxs-lookup"><span data-stu-id="713f5-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A> <span data-ttu-id="713f5-113">property</span><span class="sxs-lookup"><span data-stu-id="713f5-113">property</span></span>|<span data-ttu-id="713f5-114">Počet milisekund, po které váš program bude čekat na načítání zvuku dříve, než dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="713f5-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="713f5-115">Výchozí hodnota je 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="713f5-115">The default is 10 seconds.</span></span>|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A> <span data-ttu-id="713f5-116">property</span><span class="sxs-lookup"><span data-stu-id="713f5-116">property</span></span>|<span data-ttu-id="713f5-117">Logická hodnota označující, zda zvuk dokončení načítání.</span><span class="sxs-lookup"><span data-stu-id="713f5-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<xref:System.Media.SoundPlayer.Load%2A> <span data-ttu-id="713f5-118">– metoda</span><span class="sxs-lookup"><span data-stu-id="713f5-118">method</span></span>|<span data-ttu-id="713f5-119">Načte zvuk synchronně.</span><span class="sxs-lookup"><span data-stu-id="713f5-119">Loads a sound synchronously.</span></span>|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A> <span data-ttu-id="713f5-120">– metoda</span><span class="sxs-lookup"><span data-stu-id="713f5-120">method</span></span>|<span data-ttu-id="713f5-121">Zahájí asynchronní načítání zvuku.</span><span class="sxs-lookup"><span data-stu-id="713f5-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="713f5-122">Po dokončení načítání se vyvolá <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> událostí.</span><span class="sxs-lookup"><span data-stu-id="713f5-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<xref:System.Media.SoundPlayer.Play%2A> <span data-ttu-id="713f5-123">– metoda</span><span class="sxs-lookup"><span data-stu-id="713f5-123">method</span></span>|<span data-ttu-id="713f5-124">Přehraje zvuk podle <xref:System.Media.SoundPlayer.SoundLocation%2A> nebo <xref:System.Media.SoundPlayer.Stream%2A> vlastnost v nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="713f5-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<xref:System.Media.SoundPlayer.PlaySync%2A> <span data-ttu-id="713f5-125">– metoda</span><span class="sxs-lookup"><span data-stu-id="713f5-125">method</span></span>|<span data-ttu-id="713f5-126">Přehraje zvuk podle <xref:System.Media.SoundPlayer.SoundLocation%2A> nebo <xref:System.Media.SoundPlayer.Stream%2A> vlastnost v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="713f5-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<xref:System.Media.SoundPlayer.Stop%2A> <span data-ttu-id="713f5-127">– metoda</span><span class="sxs-lookup"><span data-stu-id="713f5-127">method</span></span>|<span data-ttu-id="713f5-128">Zastaví všechny aktuálně přehrávání zvuku.</span><span class="sxs-lookup"><span data-stu-id="713f5-128">Stops any sound currently playing.</span></span>|  
|<xref:System.Media.SoundPlayer.LoadCompleted> <span data-ttu-id="713f5-129">event</span><span class="sxs-lookup"><span data-stu-id="713f5-129">event</span></span>|<span data-ttu-id="713f5-130">Je aktivována po pokusu o načtení zvuk.</span><span class="sxs-lookup"><span data-stu-id="713f5-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="713f5-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="713f5-131">See also</span></span>

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
