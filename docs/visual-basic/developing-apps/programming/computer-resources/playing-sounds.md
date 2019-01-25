---
title: Přehrávání zvuků (Visual Basic)
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
ms.openlocfilehash: f303687fb86e23191727df769af52811a93fe71e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715787"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="af344-102">Přehrávání zvuků (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af344-102">Playing Sounds (Visual Basic)</span></span>
<span data-ttu-id="af344-103">`My.Computer.Audio` Objekt, který poskytuje metody pro přehrávání zvuku.</span><span class="sxs-lookup"><span data-stu-id="af344-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="af344-104">Přehrávání zvuků</span><span class="sxs-lookup"><span data-stu-id="af344-104">Playing Sounds</span></span>  
 <span data-ttu-id="af344-105">Přehrávání na pozadí umožňuje aplikaci spustit další kód během přehrávání zvuku.</span><span class="sxs-lookup"><span data-stu-id="af344-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="af344-106">`My.Computer.Audio.Play` Metody umožňuje, aby aplikace k přehrání zvuku pozadí pouze jeden po druhém, když aplikace přehraje zvuk nové na pozadí, zastaví přehrávání zvuku na pozadí předchozí.</span><span class="sxs-lookup"><span data-stu-id="af344-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="af344-107">Můžete přehrát zvuk a počkejte na její dokončení.</span><span class="sxs-lookup"><span data-stu-id="af344-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="af344-108">V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk.</span><span class="sxs-lookup"><span data-stu-id="af344-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="af344-109">Když `AudioPlayMode.WaitToComplete` není zadána, `My.Computer.Audio.Play` počká, dokud nebudou zvuk až po dokončení předchozího volání kódu pokračuje.</span><span class="sxs-lookup"><span data-stu-id="af344-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="af344-110">Při použití v tomto příkladu, měli byste zajistit, že název souboru odkazuje na WAV zvukový soubor, který je v počítači</span><span class="sxs-lookup"><span data-stu-id="af344-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 <span data-ttu-id="af344-111">V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk.</span><span class="sxs-lookup"><span data-stu-id="af344-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="af344-112">Při použití v tomto příkladu, měli byste zajistit, že prostředky aplikace obsahují WAV zvukový soubor, který je pojmenován vodopádu.</span><span class="sxs-lookup"><span data-stu-id="af344-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="af344-113">Přehrávání zvuků opakování ve smyčce</span><span class="sxs-lookup"><span data-stu-id="af344-113">Playing Looping Sounds</span></span>  
 <span data-ttu-id="af344-114">V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk zadaný na pozadí při `PlayMode.BackgroundLoop` je zadán.</span><span class="sxs-lookup"><span data-stu-id="af344-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="af344-115">Při použití v tomto příkladu, měli byste zajistit, že název souboru odkazuje na WAV zvukový soubor, který je ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="af344-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 <span data-ttu-id="af344-116">V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk zadaný na pozadí při `PlayMode.BackgroundLoop` je zadán.</span><span class="sxs-lookup"><span data-stu-id="af344-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="af344-117">Při použití v tomto příkladu, měli byste zajistit, že prostředky aplikace obsahují WAV zvukový soubor, který je pojmenován vodopádu.</span><span class="sxs-lookup"><span data-stu-id="af344-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 <span data-ttu-id="af344-118">V předchozím příkladu kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="af344-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="af344-119">V dialogu pro výběr fragmentu kódu je umístěn v **formulářových aplikací Windows > Zvuk**.</span><span class="sxs-lookup"><span data-stu-id="af344-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="af344-120">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="af344-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="af344-121">Obecně platí když aplikace přehrává ve smyčce zvuk, měla by nakonec zastavit zvuk.</span><span class="sxs-lookup"><span data-stu-id="af344-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="af344-122">Zastavení přehrávání zvuků na pozadí</span><span class="sxs-lookup"><span data-stu-id="af344-122">Stopping the Playing of Sounds in the Background</span></span>  
 <span data-ttu-id="af344-123">Použití `My.Computer.Audio.Stop` metoda zastavení aplikace přehrávaný na pozadí nebo opakování ve smyčce zvuk.</span><span class="sxs-lookup"><span data-stu-id="af344-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="af344-124">Obecně platí když aplikace přehrává ve smyčce zvuk, by se měla zastavit zvuk v určitém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="af344-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="af344-125">Následující příklad zastaví zvuk, který je přehrávání na pozadí.</span><span class="sxs-lookup"><span data-stu-id="af344-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 <span data-ttu-id="af344-126">V předchozím příkladu kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="af344-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="af344-127">V dialogu pro výběr fragmentu kódu je umístěn v **formulářových aplikací Windows > Zvuk**.</span><span class="sxs-lookup"><span data-stu-id="af344-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="af344-128">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="af344-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="af344-129">Přehrávání zvuků systému</span><span class="sxs-lookup"><span data-stu-id="af344-129">Playing System Sounds</span></span>  
 <span data-ttu-id="af344-130">Použití `My.Computer.Audio.PlaySystemSound` metodu pro zadaný systém přehrávat zvuk.</span><span class="sxs-lookup"><span data-stu-id="af344-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="af344-131">`My.Computer.Audio.PlaySystemSound` Metoda přebírá jako parametr jeden sdílené členy z <xref:System.Media.SystemSound> třídy.</span><span class="sxs-lookup"><span data-stu-id="af344-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="af344-132">Systémového zvuku <xref:System.Media.SystemSounds.Asterisk%2A> obvykle označuje chybu.</span><span class="sxs-lookup"><span data-stu-id="af344-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="af344-133">V následujícím příkladu `My.Computer.Audio.PlaySystemSound` metoda přehrát zvuk systému.</span><span class="sxs-lookup"><span data-stu-id="af344-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="af344-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af344-134">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
