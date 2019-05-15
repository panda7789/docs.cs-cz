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
ms.openlocfilehash: e14d9de2326234b86c1f24b227e86f822fbfdb71
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592356"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="e40e8-102">Postupy: Opakované přehrávání zvuku ve formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e40e8-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="e40e8-103">Následující příklad kódu opakovaně přehraje zvuk.</span><span class="sxs-lookup"><span data-stu-id="e40e8-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="e40e8-104">Když kód v `stopPlayingButton_Click` spustí obslužnou rutinu události, všechny aktuálně přehrávání zastaví zvuku.</span><span class="sxs-lookup"><span data-stu-id="e40e8-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="e40e8-105">Pokud žádný zvukový signál přehrávání, nic se nestane.</span><span class="sxs-lookup"><span data-stu-id="e40e8-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e40e8-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e40e8-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e40e8-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e40e8-107">Compiling the Code</span></span>  
 <span data-ttu-id="e40e8-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e40e8-108">This example requires:</span></span>  
  
- <span data-ttu-id="e40e8-109">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e40e8-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="e40e8-110">Nahradit název souboru `"c:\Windows\Media\chimes.wav"` s platným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="e40e8-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e40e8-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="e40e8-111">Robust Programming</span></span>  
 <span data-ttu-id="e40e8-112">Operace se soubory by měl být uzavřen v rámci příslušné zpracování výjimek bloků.</span><span class="sxs-lookup"><span data-stu-id="e40e8-112">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="e40e8-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="e40e8-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="e40e8-114">Název cesty je poškozený.</span><span class="sxs-lookup"><span data-stu-id="e40e8-114">The path name is malformed.</span></span> <span data-ttu-id="e40e8-115">Například obsahuje neplatné znaky nebo je prázdné znaky (<xref:System.ArgumentException> třídy).</span><span class="sxs-lookup"><span data-stu-id="e40e8-115">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
- <span data-ttu-id="e40e8-116">Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).</span><span class="sxs-lookup"><span data-stu-id="e40e8-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="e40e8-117">Název cesty je `Nothing` (<xref:System.ArgumentNullException> třídy).</span><span class="sxs-lookup"><span data-stu-id="e40e8-117">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="e40e8-118">Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="e40e8-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="e40e8-119">Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třídy).</span><span class="sxs-lookup"><span data-stu-id="e40e8-119">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
- <span data-ttu-id="e40e8-120">Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException> třídy).</span><span class="sxs-lookup"><span data-stu-id="e40e8-120">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e40e8-121">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e40e8-121">.NET Framework Security</span></span>  
 <span data-ttu-id="e40e8-122">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="e40e8-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="e40e8-123">Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e40e8-123">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="e40e8-124">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="e40e8-124">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40e8-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e40e8-125">See also</span></span>

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [<span data-ttu-id="e40e8-126">Postupy: Přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="e40e8-126">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="e40e8-127">Přehled třídy SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="e40e8-127">SoundPlayer Class Overview</span></span>](soundplayer-class-overview.md)
