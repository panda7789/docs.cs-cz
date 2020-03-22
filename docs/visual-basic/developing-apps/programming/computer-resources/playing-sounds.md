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
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="9011c-102">Přehrávání zvuků (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9011c-102">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="9011c-103">Objekt `My.Computer.Audio` poskytuje metody pro přehrávání zvuků.</span><span class="sxs-lookup"><span data-stu-id="9011c-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="9011c-104">Přehrávání zvuků</span><span class="sxs-lookup"><span data-stu-id="9011c-104">Playing Sounds</span></span>  

 <span data-ttu-id="9011c-105">Přehrávání na pozadí umožňuje aplikaci spustit jiný kód, zatímco zvuk hraje.</span><span class="sxs-lookup"><span data-stu-id="9011c-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="9011c-106">Metoda `My.Computer.Audio.Play` umožňuje aplikaci přehrávat pouze jeden zvuk na pozadí najednou; když aplikace přehraje nový zvuk na pozadí, přestane přehrávat předchozí zvuk na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9011c-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="9011c-107">Můžete také přehrát zvuk a počkat na jeho dokončení.</span><span class="sxs-lookup"><span data-stu-id="9011c-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="9011c-108">V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk.</span><span class="sxs-lookup"><span data-stu-id="9011c-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="9011c-109">Pokud `AudioPlayMode.WaitToComplete` je `My.Computer.Audio.Play` zadán, čeká na dokončení zvuku před pokračováním volání kódu.</span><span class="sxs-lookup"><span data-stu-id="9011c-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="9011c-110">Při použití tohoto příkladu byste měli zajistit, aby název souboru odkazoval na zvukový soubor WAV, který je v počítači</span><span class="sxs-lookup"><span data-stu-id="9011c-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="9011c-111">V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk.</span><span class="sxs-lookup"><span data-stu-id="9011c-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="9011c-112">Při použití tohoto příkladu byste měli zajistit, aby prostředky aplikace obsahovaly zvukový soubor WAV s názvem Waterfall.</span><span class="sxs-lookup"><span data-stu-id="9011c-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="9011c-113">Přehrávání zvuků smyčky</span><span class="sxs-lookup"><span data-stu-id="9011c-113">Playing Looping Sounds</span></span>  

 <span data-ttu-id="9011c-114">V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zadaný `PlayMode.BackgroundLoop` zvuk na pozadí, když je zadán.</span><span class="sxs-lookup"><span data-stu-id="9011c-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="9011c-115">Při použití tohoto příkladu byste měli zajistit, aby název souboru odkazoval na zvukový soubor WAV, který je v počítači.</span><span class="sxs-lookup"><span data-stu-id="9011c-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="9011c-116">V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zadaný `PlayMode.BackgroundLoop` zvuk na pozadí, když je zadán.</span><span class="sxs-lookup"><span data-stu-id="9011c-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="9011c-117">Při použití tohoto příkladu byste měli zajistit, aby prostředky aplikace obsahovaly zvukový soubor WAV s názvem Waterfall.</span><span class="sxs-lookup"><span data-stu-id="9011c-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="9011c-118">Předchozí příklad kódu je také k dispozici jako fragment kódu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="9011c-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="9011c-119">Ve výběru fragmentu kódu je umístěn v **aplikacích Windows Forms > Sound**.</span><span class="sxs-lookup"><span data-stu-id="9011c-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="9011c-120">Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="9011c-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="9011c-121">Obecně platí, že když aplikace přehrává zvuk opakování, měla by nakonec zvuk zastavit.</span><span class="sxs-lookup"><span data-stu-id="9011c-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="9011c-122">Zastavení přehrávání zvuků na pozadí</span><span class="sxs-lookup"><span data-stu-id="9011c-122">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="9011c-123">Pomocí `My.Computer.Audio.Stop` této metody můžete zastavit aktuálně přehrávaný zvuk aplikace nebo zvuk opakování.</span><span class="sxs-lookup"><span data-stu-id="9011c-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="9011c-124">Obecně platí, že když aplikace přehrává zvuk opakování, měla by v určitém okamžiku zvuk zastavit.</span><span class="sxs-lookup"><span data-stu-id="9011c-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="9011c-125">Následující příklad zastaví zvuk, který se přehrává na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9011c-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="9011c-126">Předchozí příklad kódu je také k dispozici jako fragment kódu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="9011c-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="9011c-127">Ve výběru fragmentu kódu je umístěn v **aplikacích Windows Forms > Sound**.</span><span class="sxs-lookup"><span data-stu-id="9011c-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="9011c-128">Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="9011c-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="9011c-129">Přehrávání systémových zvuků</span><span class="sxs-lookup"><span data-stu-id="9011c-129">Playing System Sounds</span></span>  

 <span data-ttu-id="9011c-130">Pomocí `My.Computer.Audio.PlaySystemSound` této metody přehrajte zadaný systémový zvuk.</span><span class="sxs-lookup"><span data-stu-id="9011c-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="9011c-131">Metoda `My.Computer.Audio.PlaySystemSound` bere jako parametr jeden ze sdílených členů z třídy. <xref:System.Media.SystemSound></span><span class="sxs-lookup"><span data-stu-id="9011c-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="9011c-132">Systémový <xref:System.Media.SystemSounds.Asterisk%2A> zvuk obecně označuje chyby.</span><span class="sxs-lookup"><span data-stu-id="9011c-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="9011c-133">Následující příklad používá `My.Computer.Audio.PlaySystemSound` metodu k přehrávání systémového zvuku.</span><span class="sxs-lookup"><span data-stu-id="9011c-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="9011c-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="9011c-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
