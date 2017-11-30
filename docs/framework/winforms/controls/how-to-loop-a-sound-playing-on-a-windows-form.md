---
title: "Postupy: Opakované přehrávání zvuku ve formuláři Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e61a15a7a249a90ce9eca035ebe6fd67275bb74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="f2969-102">Postupy: Opakované přehrávání zvuku ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="f2969-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="f2969-103">Následující příklad kódu opakovaného hraje zvuku.</span><span class="sxs-lookup"><span data-stu-id="f2969-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="f2969-104">Když kód v `stopPlayingButton_Click` spuštění obslužné rutiny události, zvuk, který se aktuálně přehrávání zastaví.</span><span class="sxs-lookup"><span data-stu-id="f2969-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="f2969-105">Pokud žádné přehrávání zvuku, nedojde k žádné akci.</span><span class="sxs-lookup"><span data-stu-id="f2969-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2969-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2969-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f2969-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f2969-107">Compiling the Code</span></span>  
 <span data-ttu-id="f2969-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f2969-108">This example requires:</span></span>  
  
-   <span data-ttu-id="f2969-109">Odkazy na systém a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2969-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="f2969-110">Nahradit název souboru `"c:\Windows\Media\chimes.wav"` s platný název souboru.</span><span class="sxs-lookup"><span data-stu-id="f2969-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="f2969-111">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f2969-111">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f2969-112">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="f2969-112">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="f2969-113">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f2969-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f2969-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f2969-114">Robust Programming</span></span>  
 <span data-ttu-id="f2969-115">Operace se soubory by měl být uzavřena v příslušné bloky zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="f2969-115">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="f2969-116">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="f2969-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f2969-117">Název cesty je chybný.</span><span class="sxs-lookup"><span data-stu-id="f2969-117">The path name is malformed.</span></span> <span data-ttu-id="f2969-118">Například obsahuje znaky, které nejsou platné nebo je pouze mezera (<xref:System.ArgumentException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f2969-118">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="f2969-119">Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f2969-119">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="f2969-120">Název cesty je `Nothing` (<xref:System.ArgumentNullException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f2969-120">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="f2969-121">Cesta je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f2969-121">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="f2969-122">Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f2969-122">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="f2969-123">Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f2969-123">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f2969-124">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f2969-124">.NET Framework Security</span></span>  
 <span data-ttu-id="f2969-125">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="f2969-125">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="f2969-126">Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f2969-126">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="f2969-127">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="f2969-127">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2969-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2969-128">See Also</span></span>  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>  
 [<span data-ttu-id="f2969-129">Postupy: přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="f2969-129">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="f2969-130">Přehled třídy SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="f2969-130">SoundPlayer Class Overview</span></span>](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
