---
title: 'Postupy: Asynchronní načítání zvuku ve formuláři Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 5f533d82fcca07a2b64bdbbfb160a7b2a23ce540
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592372"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="68e1d-102">Postupy: Asynchronní načítání zvuku ve formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="68e1d-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="68e1d-103">Následující příklad kódu asynchronně načte zvuk z adresy URL a pak hraje v novém vláknu.</span><span class="sxs-lookup"><span data-stu-id="68e1d-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68e1d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="68e1d-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68e1d-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="68e1d-105">Compiling the Code</span></span>  
 <span data-ttu-id="68e1d-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="68e1d-106">This example requires:</span></span>  
  
- <span data-ttu-id="68e1d-107">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="68e1d-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="68e1d-108">Nahradit název souboru `"http://www.tailspintoys.com/sounds/stop.wav"` s platným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="68e1d-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="68e1d-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="68e1d-109">Robust Programming</span></span>  
 <span data-ttu-id="68e1d-110">Operace se soubory by měl být uzavřen v rámci příslušné zpracování výjimek bloků.</span><span class="sxs-lookup"><span data-stu-id="68e1d-110">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="68e1d-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="68e1d-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="68e1d-112">Název cesty je poškozený.</span><span class="sxs-lookup"><span data-stu-id="68e1d-112">The path name is malformed.</span></span> <span data-ttu-id="68e1d-113">Například obsahuje znaky, které nejsou platné nebo je prázdné znaky (<xref:System.ArgumentException> třídy).</span><span class="sxs-lookup"><span data-stu-id="68e1d-113">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
- <span data-ttu-id="68e1d-114">Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).</span><span class="sxs-lookup"><span data-stu-id="68e1d-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="68e1d-115">Název cesty je `Nothing` (<xref:System.ArgumentNullException> třídy).</span><span class="sxs-lookup"><span data-stu-id="68e1d-115">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="68e1d-116">Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="68e1d-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="68e1d-117">Cesta není platná (<xref:System.IO.DirectoryNotFoundException> třídy).</span><span class="sxs-lookup"><span data-stu-id="68e1d-117">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
- <span data-ttu-id="68e1d-118">Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException> třídy).</span><span class="sxs-lookup"><span data-stu-id="68e1d-118">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="68e1d-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="68e1d-119">.NET Framework Security</span></span>  
 <span data-ttu-id="68e1d-120">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="68e1d-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="68e1d-121">Například soubor `Form1.vb` nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="68e1d-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="68e1d-122">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="68e1d-122">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e1d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68e1d-123">See also</span></span>

- <xref:System.Media.SoundPlayer.LoadAsync%2A>
- <xref:System.Media.SoundPlayer.LoadCompleted>
- <xref:System.Media.SoundPlayer.Play%2A>
- [<span data-ttu-id="68e1d-124">Postupy: Přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="68e1d-124">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
