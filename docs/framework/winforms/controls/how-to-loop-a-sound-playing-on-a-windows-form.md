---
title: 'Postupy: Opakované přehrávání zvuku ve formuláři Windows Forms'
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
ms.openlocfilehash: a74acbbbcb5646a35de54a6000a0feae30f145a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638904"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="8d86c-102">Postupy: Opakované přehrávání zvuku ve formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d86c-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="8d86c-103">Následující příklad kódu opakovaně přehraje zvuk.</span><span class="sxs-lookup"><span data-stu-id="8d86c-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="8d86c-104">Když kód v `stopPlayingButton_Click` spustí obslužnou rutinu události, všechny aktuálně přehrávání zastaví zvuku.</span><span class="sxs-lookup"><span data-stu-id="8d86c-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="8d86c-105">Pokud žádný zvukový signál přehrávání, nic se nestane.</span><span class="sxs-lookup"><span data-stu-id="8d86c-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d86c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d86c-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8d86c-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8d86c-107">Compiling the Code</span></span>  
 <span data-ttu-id="8d86c-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="8d86c-108">This example requires:</span></span>  
  
- <span data-ttu-id="8d86c-109">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="8d86c-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="8d86c-110">Nahradit název souboru `"c:\Windows\Media\chimes.wav"` s platným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="8d86c-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="8d86c-111">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8d86c-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8d86c-112">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="8d86c-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8d86c-113">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="8d86c-113">Robust Programming</span></span>  
 <span data-ttu-id="8d86c-114">Operace se soubory by měl být uzavřen v rámci příslušné zpracování výjimek bloků.</span><span class="sxs-lookup"><span data-stu-id="8d86c-114">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="8d86c-115">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="8d86c-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8d86c-116">Název cesty je poškozený.</span><span class="sxs-lookup"><span data-stu-id="8d86c-116">The path name is malformed.</span></span> <span data-ttu-id="8d86c-117">Například obsahuje neplatné znaky nebo je prázdné znaky (<xref:System.ArgumentException> třídy).</span><span class="sxs-lookup"><span data-stu-id="8d86c-117">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
- <span data-ttu-id="8d86c-118">Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).</span><span class="sxs-lookup"><span data-stu-id="8d86c-118">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="8d86c-119">Název cesty je `Nothing` (<xref:System.ArgumentNullException> třídy).</span><span class="sxs-lookup"><span data-stu-id="8d86c-119">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="8d86c-120">Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="8d86c-120">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="8d86c-121">Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třídy).</span><span class="sxs-lookup"><span data-stu-id="8d86c-121">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
- <span data-ttu-id="8d86c-122">Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException> třídy).</span><span class="sxs-lookup"><span data-stu-id="8d86c-122">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8d86c-123">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8d86c-123">.NET Framework Security</span></span>  
 <span data-ttu-id="8d86c-124">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="8d86c-124">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="8d86c-125">Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8d86c-125">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="8d86c-126">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="8d86c-126">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d86c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d86c-127">See also</span></span>

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [<span data-ttu-id="8d86c-128">Postupy: Přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="8d86c-128">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="8d86c-129">Přehled třídy SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="8d86c-129">SoundPlayer Class Overview</span></span>](soundplayer-class-overview.md)
