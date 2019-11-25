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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345525"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="c15a8-102">Přehrávání zvuků (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c15a8-102">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="c15a8-103">The `My.Computer.Audio` object provides methods for playing sounds.</span><span class="sxs-lookup"><span data-stu-id="c15a8-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="c15a8-104">Přehrávání zvuků</span><span class="sxs-lookup"><span data-stu-id="c15a8-104">Playing Sounds</span></span>  

 <span data-ttu-id="c15a8-105">Background playing lets the application execute other code while the sound plays.</span><span class="sxs-lookup"><span data-stu-id="c15a8-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="c15a8-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span><span class="sxs-lookup"><span data-stu-id="c15a8-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="c15a8-107">You can also play a sound and wait for it to complete.</span><span class="sxs-lookup"><span data-stu-id="c15a8-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="c15a8-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span><span class="sxs-lookup"><span data-stu-id="c15a8-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="c15a8-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span><span class="sxs-lookup"><span data-stu-id="c15a8-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="c15a8-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span><span class="sxs-lookup"><span data-stu-id="c15a8-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="c15a8-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span><span class="sxs-lookup"><span data-stu-id="c15a8-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="c15a8-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span><span class="sxs-lookup"><span data-stu-id="c15a8-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="c15a8-113">Playing Looping Sounds</span><span class="sxs-lookup"><span data-stu-id="c15a8-113">Playing Looping Sounds</span></span>  

 <span data-ttu-id="c15a8-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span><span class="sxs-lookup"><span data-stu-id="c15a8-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="c15a8-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span><span class="sxs-lookup"><span data-stu-id="c15a8-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="c15a8-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span><span class="sxs-lookup"><span data-stu-id="c15a8-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="c15a8-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span><span class="sxs-lookup"><span data-stu-id="c15a8-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="c15a8-118">The preceding code example is also available as an IntelliSense code snippet.</span><span class="sxs-lookup"><span data-stu-id="c15a8-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c15a8-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span><span class="sxs-lookup"><span data-stu-id="c15a8-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="c15a8-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c15a8-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="c15a8-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span><span class="sxs-lookup"><span data-stu-id="c15a8-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="c15a8-122">Stopping the Playing of Sounds in the Background</span><span class="sxs-lookup"><span data-stu-id="c15a8-122">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="c15a8-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span><span class="sxs-lookup"><span data-stu-id="c15a8-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="c15a8-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span><span class="sxs-lookup"><span data-stu-id="c15a8-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="c15a8-125">The following example stops a sound that is playing in the background.</span><span class="sxs-lookup"><span data-stu-id="c15a8-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="c15a8-126">The preceding code example is also available as an IntelliSense code snippet.</span><span class="sxs-lookup"><span data-stu-id="c15a8-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c15a8-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span><span class="sxs-lookup"><span data-stu-id="c15a8-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="c15a8-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c15a8-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="c15a8-129">Playing System Sounds</span><span class="sxs-lookup"><span data-stu-id="c15a8-129">Playing System Sounds</span></span>  

 <span data-ttu-id="c15a8-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span><span class="sxs-lookup"><span data-stu-id="c15a8-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="c15a8-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span><span class="sxs-lookup"><span data-stu-id="c15a8-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="c15a8-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span><span class="sxs-lookup"><span data-stu-id="c15a8-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="c15a8-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span><span class="sxs-lookup"><span data-stu-id="c15a8-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="c15a8-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c15a8-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
