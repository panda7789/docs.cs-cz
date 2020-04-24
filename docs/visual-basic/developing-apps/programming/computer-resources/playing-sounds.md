---
title: Přehrávání zvuků
ms.date: 07/20/2015
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
ms.openlocfilehash: 416fedd011ff35d2b32d1b64932e3908a73ed14e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345525"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="928dd-102">Přehrávání zvuků (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="928dd-102">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="928dd-103">`My.Computer.Audio` Objekt poskytuje metody pro přehrávání zvuků.</span><span class="sxs-lookup"><span data-stu-id="928dd-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="928dd-104">Přehrávání zvuků</span><span class="sxs-lookup"><span data-stu-id="928dd-104">Playing Sounds</span></span>  

 <span data-ttu-id="928dd-105">Přehrávání na pozadí umožňuje aplikaci při přehrávání zvuku provést jiný kód.</span><span class="sxs-lookup"><span data-stu-id="928dd-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="928dd-106">`My.Computer.Audio.Play` Metoda umožňuje, aby aplikace současně hrála pouze jeden zvuk na pozadí. Když aplikace přehraje nový zvuk na pozadí, zastaví se přehrávání předchozího zvuku na pozadí.</span><span class="sxs-lookup"><span data-stu-id="928dd-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="928dd-107">Můžete také přehrát zvuk a počkat na jeho dokončení.</span><span class="sxs-lookup"><span data-stu-id="928dd-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="928dd-108">V následujícím příkladu `My.Computer.Audio.Play` Metoda přehrává zvuk.</span><span class="sxs-lookup"><span data-stu-id="928dd-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="928dd-109">Když `AudioPlayMode.WaitToComplete` je zadáno, `My.Computer.Audio.Play` počká na dokončení zvuku před pokračováním volání kódu.</span><span class="sxs-lookup"><span data-stu-id="928dd-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="928dd-110">Při použití tohoto příkladu byste měli zkontrolovat, že název souboru odkazuje na zvukový soubor. wav, který je ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="928dd-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="928dd-111">V následujícím příkladu `My.Computer.Audio.Play` Metoda přehrává zvuk.</span><span class="sxs-lookup"><span data-stu-id="928dd-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="928dd-112">Při použití tohoto příkladu byste měli zajistit, aby prostředky aplikace zahrnovaly zvukový soubor. wav s názvem vodopád.</span><span class="sxs-lookup"><span data-stu-id="928dd-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="928dd-113">Přehrávání zvukových smyček</span><span class="sxs-lookup"><span data-stu-id="928dd-113">Playing Looping Sounds</span></span>  

 <span data-ttu-id="928dd-114">V následujícím příkladu `My.Computer.Audio.Play` metoda při `PlayMode.BackgroundLoop` zadání přehraje zadaný zvuk na pozadí.</span><span class="sxs-lookup"><span data-stu-id="928dd-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="928dd-115">Při použití tohoto příkladu byste měli zkontrolovat, že název souboru odkazuje na zvukový soubor. wav, který je ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="928dd-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="928dd-116">V následujícím příkladu `My.Computer.Audio.Play` metoda při `PlayMode.BackgroundLoop` zadání přehraje zadaný zvuk na pozadí.</span><span class="sxs-lookup"><span data-stu-id="928dd-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="928dd-117">Při použití tohoto příkladu byste měli zajistit, aby prostředky aplikace zahrnovaly zvukový soubor. wav s názvem vodopád.</span><span class="sxs-lookup"><span data-stu-id="928dd-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="928dd-118">Předchozí příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="928dd-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="928dd-119">Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > zvuku**.</span><span class="sxs-lookup"><span data-stu-id="928dd-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="928dd-120">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="928dd-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="928dd-121">Obecně platí, že když aplikace přehraje zvuk ve smyčce, měl by nakonec zastavit zvuk.</span><span class="sxs-lookup"><span data-stu-id="928dd-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="928dd-122">Zastavování přehrávání zvuků na pozadí</span><span class="sxs-lookup"><span data-stu-id="928dd-122">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="928dd-123">Použijte `My.Computer.Audio.Stop` metodu k zastavení aktuálně přehrávaného zvuku na pozadí nebo ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="928dd-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="928dd-124">Obecně platí, že když aplikace přehraje zvuk ve smyčce, měl by zastavit zvuk v nějakém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="928dd-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="928dd-125">Následující příklad zastaví zvuk, který se přehrává na pozadí.</span><span class="sxs-lookup"><span data-stu-id="928dd-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="928dd-126">Předchozí příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="928dd-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="928dd-127">Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > zvuku**.</span><span class="sxs-lookup"><span data-stu-id="928dd-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="928dd-128">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="928dd-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="928dd-129">Přehrávání systémových zvuků</span><span class="sxs-lookup"><span data-stu-id="928dd-129">Playing System Sounds</span></span>  

 <span data-ttu-id="928dd-130">Použijte `My.Computer.Audio.PlaySystemSound` metodu k přehrání zadaného systémového zvuku.</span><span class="sxs-lookup"><span data-stu-id="928dd-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="928dd-131">`My.Computer.Audio.PlaySystemSound` Metoda přebírá jako parametr jeden ze sdílených členů z <xref:System.Media.SystemSound> třídy.</span><span class="sxs-lookup"><span data-stu-id="928dd-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="928dd-132">Systémový zvuk <xref:System.Media.SystemSounds.Asterisk%2A> obecně označuje chyby.</span><span class="sxs-lookup"><span data-stu-id="928dd-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="928dd-133">Následující příklad používá `My.Computer.Audio.PlaySystemSound` metodu k přehrání systémového zvuku.</span><span class="sxs-lookup"><span data-stu-id="928dd-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="928dd-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="928dd-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
