---
title: "Přehrávání zvuků (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8be5cec634482bf99ddff4ff6b6af8e897c4909e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="8fdae-102">Přehrávání zvuků (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fdae-102">Playing Sounds (Visual Basic)</span></span>
<span data-ttu-id="8fdae-103">`My.Computer.Audio` Objekt poskytuje metody pro přehrávání zvuku.</span><span class="sxs-lookup"><span data-stu-id="8fdae-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="8fdae-104">Přehrávání zvuků</span><span class="sxs-lookup"><span data-stu-id="8fdae-104">Playing Sounds</span></span>  
 <span data-ttu-id="8fdae-105">Přehrávání pozadí umožní aplikaci provést jiný kód, během přehrávání zvuku.</span><span class="sxs-lookup"><span data-stu-id="8fdae-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="8fdae-106">`My.Computer.Audio.Play` Metoda umožňuje aplikaci přehrát zvuk pouze jeden pozadí najednou; aplikace na nové pozadí přehrává zvuk, zastaví, přehrávání zvuku předchozí pozadí.</span><span class="sxs-lookup"><span data-stu-id="8fdae-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="8fdae-107">Také můžete přehrát zvuk a počkejte na její dokončení.</span><span class="sxs-lookup"><span data-stu-id="8fdae-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="8fdae-108">V následujícím příkladu `My.Computer.Audio.Play` metoda hraje zvuku.</span><span class="sxs-lookup"><span data-stu-id="8fdae-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="8fdae-109">Když `AudioPlayMode.WaitToComplete` není zadaný, `My.Computer.Audio.Play` čeká, až do dokončení zvuk než volání kódu dál.</span><span class="sxs-lookup"><span data-stu-id="8fdae-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="8fdae-110">Při použití v tomto příkladu, by měl zajistěte, že název souboru odkazovala na zvukový soubor ve formátu WAV, který je v počítači</span><span class="sxs-lookup"><span data-stu-id="8fdae-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 <span data-ttu-id="8fdae-111">V následujícím příkladu `My.Computer.Audio.Play` metoda hraje zvuku.</span><span class="sxs-lookup"><span data-stu-id="8fdae-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="8fdae-112">Při použití v tomto příkladu, ujistěte se, že prostředky aplikace obsahují zvukový soubor ve formátu WAV s názvem vodopádu.</span><span class="sxs-lookup"><span data-stu-id="8fdae-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="8fdae-113">Přehrávání zvuků ve smyčce</span><span class="sxs-lookup"><span data-stu-id="8fdae-113">Playing Looping Sounds</span></span>  
 <span data-ttu-id="8fdae-114">V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje určený zvuk na pozadí při `PlayMode.BackgroundLoop` je zadán.</span><span class="sxs-lookup"><span data-stu-id="8fdae-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="8fdae-115">Při použití v tomto příkladu, ujistěte se, že název souboru odkazuje na zvukový soubor ve formátu WAV, který je ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="8fdae-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 <span data-ttu-id="8fdae-116">V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje určený zvuk na pozadí při `PlayMode.BackgroundLoop` je zadán.</span><span class="sxs-lookup"><span data-stu-id="8fdae-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="8fdae-117">Při použití v tomto příkladu, ujistěte se, že prostředky aplikace obsahují zvukový soubor ve formátu WAV s názvem vodopádu.</span><span class="sxs-lookup"><span data-stu-id="8fdae-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 <span data-ttu-id="8fdae-118">V předchozím příkladu kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="8fdae-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="8fdae-119">V Sběrač fragmentů kódu je umístěn v **aplikacích Windows Forms > Zvuk**.</span><span class="sxs-lookup"><span data-stu-id="8fdae-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="8fdae-120">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="8fdae-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="8fdae-121">Obecně platí když aplikace přehraje opakování zvuk, měla by nakonec zastavit zvuk.</span><span class="sxs-lookup"><span data-stu-id="8fdae-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="8fdae-122">Zastavení přehrávání zvuků na pozadí</span><span class="sxs-lookup"><span data-stu-id="8fdae-122">Stopping the Playing of Sounds in the Background</span></span>  
 <span data-ttu-id="8fdae-123">Použití `My.Computer.Audio.Stop` metoda zastavení aplikace aktuálně přehrávání pozadí nebo opakování ve smyčce zvuku.</span><span class="sxs-lookup"><span data-stu-id="8fdae-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="8fdae-124">Obecně platí když aplikace přehraje opakování zvuk, by se měla zastavit zvuk v určitém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="8fdae-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="8fdae-125">Následující příklad zastaví zvuk, který je přehrávání na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8fdae-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 <span data-ttu-id="8fdae-126">V předchozím příkladu kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="8fdae-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="8fdae-127">V Sběrač fragmentů kódu je umístěn v **aplikacích Windows Forms > Zvuk**.</span><span class="sxs-lookup"><span data-stu-id="8fdae-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="8fdae-128">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="8fdae-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="8fdae-129">Přehrávání zvuků systému</span><span class="sxs-lookup"><span data-stu-id="8fdae-129">Playing System Sounds</span></span>  
 <span data-ttu-id="8fdae-130">Použití `My.Computer.Audio.PlaySystemSound` metoda přehrát zvuk zadaný systém.</span><span class="sxs-lookup"><span data-stu-id="8fdae-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="8fdae-131">`My.Computer.Audio.PlaySystemSound` Metoda přebírá jako parametr jednoho sdíleného člena z <xref:System.Media.SystemSound> třídy.</span><span class="sxs-lookup"><span data-stu-id="8fdae-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="8fdae-132">Systémového zvuku <xref:System.Media.SystemSounds.Asterisk%2A> obvykle označuje chybu.</span><span class="sxs-lookup"><span data-stu-id="8fdae-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="8fdae-133">Následující příklad používá `My.Computer.Audio.PlaySystemSound` metoda přehrát zvuk systému.</span><span class="sxs-lookup"><span data-stu-id="8fdae-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8fdae-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="8fdae-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Audio>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>  
 <xref:Microsoft.VisualBasic.AudioPlayMode>
