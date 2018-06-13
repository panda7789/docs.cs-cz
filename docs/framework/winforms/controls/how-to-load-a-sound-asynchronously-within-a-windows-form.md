---
title: 'Postupy: Asynchronní načítání zvuku ve formuláři Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 9ebede03a3a9d2cc6db1cda2537bcaf30afcb2d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533566"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="f87c4-102">Postupy: Asynchronní načítání zvuku ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="f87c4-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="f87c4-103">Následující příklad kódu asynchronně načte zvuku z adresy URL a pak ho hraje na nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="f87c4-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f87c4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f87c4-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f87c4-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f87c4-105">Compiling the Code</span></span>  
 <span data-ttu-id="f87c4-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f87c4-106">This example requires:</span></span>  
  
-   <span data-ttu-id="f87c4-107">Odkazy na systém a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="f87c4-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="f87c4-108">Nahradit název souboru `"http://www.tailspintoys.com/sounds/stop.wav"` s platný název souboru.</span><span class="sxs-lookup"><span data-stu-id="f87c4-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="f87c4-109">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f87c4-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f87c4-110">Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="f87c4-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f87c4-111">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f87c4-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f87c4-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f87c4-112">Robust Programming</span></span>  
 <span data-ttu-id="f87c4-113">Operace se soubory by měl být uzavřena v příslušné bloky zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="f87c4-113">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="f87c4-114">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="f87c4-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f87c4-115">Název cesty je chybný.</span><span class="sxs-lookup"><span data-stu-id="f87c4-115">The path name is malformed.</span></span> <span data-ttu-id="f87c4-116">Například obsahuje znaky, které nejsou platné nebo je pouze mezera (<xref:System.ArgumentException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f87c4-116">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="f87c4-117">Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f87c4-117">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="f87c4-118">Název cesty je `Nothing` (<xref:System.ArgumentNullException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f87c4-118">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="f87c4-119">Cesta je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f87c4-119">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="f87c4-120">Cesta není platná (<xref:System.IO.DirectoryNotFoundException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f87c4-120">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="f87c4-121">Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f87c4-121">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f87c4-122">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f87c4-122">.NET Framework Security</span></span>  
 <span data-ttu-id="f87c4-123">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="f87c4-123">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="f87c4-124">Například soubor `Form1.vb` nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f87c4-124">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="f87c4-125">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="f87c4-125">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f87c4-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f87c4-126">See Also</span></span>  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <xref:System.Media.SoundPlayer.LoadCompleted>  
 <xref:System.Media.SoundPlayer.Play%2A>  
 [<span data-ttu-id="f87c4-127">Postupy: Přehrávání zvuku z formuláře Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f87c4-127">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
