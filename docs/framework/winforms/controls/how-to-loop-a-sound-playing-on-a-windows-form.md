---
title: 'Postupy: Smyčka přehrávání zvuku ve formuláři Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
ms.openlocfilehash: 93793fae418b33c954c9d597f020c8daf8cfedfd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493401"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="57be1-102">Postupy: Smyčka přehrávání zvuku ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="57be1-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="57be1-103">Následující příklad kódu opakovaně přehraje zvuk.</span><span class="sxs-lookup"><span data-stu-id="57be1-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="57be1-104">Když kód v `stopPlayingButton_Click` spustí obslužnou rutinu události, všechny aktuálně přehrávání zastaví zvuku.</span><span class="sxs-lookup"><span data-stu-id="57be1-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="57be1-105">Pokud žádný zvukový signál přehrávání, nic se nestane.</span><span class="sxs-lookup"><span data-stu-id="57be1-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57be1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="57be1-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="57be1-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="57be1-107">Compiling the Code</span></span>  
 <span data-ttu-id="57be1-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="57be1-108">This example requires:</span></span>  
  
-   <span data-ttu-id="57be1-109">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="57be1-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="57be1-110">Nahradit název souboru `"c:\Windows\Media\chimes.wav"` s platným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="57be1-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="57be1-111">Informace o vytváření použijeme příklad z příkazového řádku pro visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="57be1-111">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="57be1-112">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="57be1-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="57be1-113">Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="57be1-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="57be1-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="57be1-114">Robust Programming</span></span>  
 <span data-ttu-id="57be1-115">Operace se soubory by měl být uzavřen v rámci příslušné zpracování výjimek bloků.</span><span class="sxs-lookup"><span data-stu-id="57be1-115">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="57be1-116">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="57be1-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="57be1-117">Název cesty je poškozený.</span><span class="sxs-lookup"><span data-stu-id="57be1-117">The path name is malformed.</span></span> <span data-ttu-id="57be1-118">Například obsahuje neplatné znaky nebo je prázdné znaky (<xref:System.ArgumentException> třídy).</span><span class="sxs-lookup"><span data-stu-id="57be1-118">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="57be1-119">Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).</span><span class="sxs-lookup"><span data-stu-id="57be1-119">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="57be1-120">Název cesty je `Nothing` (<xref:System.ArgumentNullException> třídy).</span><span class="sxs-lookup"><span data-stu-id="57be1-120">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="57be1-121">Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="57be1-121">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="57be1-122">Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třídy).</span><span class="sxs-lookup"><span data-stu-id="57be1-122">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="57be1-123">Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException> třídy).</span><span class="sxs-lookup"><span data-stu-id="57be1-123">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="57be1-124">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="57be1-124">.NET Framework Security</span></span>  
 <span data-ttu-id="57be1-125">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="57be1-125">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="57be1-126">Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="57be1-126">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="57be1-127">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="57be1-127">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57be1-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57be1-128">See also</span></span>
- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [<span data-ttu-id="57be1-129">Postupy: Přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="57be1-129">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="57be1-130">Přehled třídy SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="57be1-130">SoundPlayer Class Overview</span></span>](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
