---
title: 'Postupy: Přehrávání zvuku z formuláře Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
ms.openlocfilehash: 02b0cb2952e11946f994819bb09a55167781137c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607248"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="f6ca8-102">Postupy: Přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="f6ca8-102">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="f6ca8-103">V tomto příkladu přehraje zvuk v dané cestě v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f6ca8-103">This example plays a sound at a given path at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6ca8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6ca8-104">Example</span></span>  
  
```vb  
Sub PlaySimpleSound()  
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")  
End Sub  
```  
  
```csharp  
private void playSimpleSound()  
{  
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");  
    simpleSound.Play();  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6ca8-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f6ca8-105">Compiling the Code</span></span>  
 <span data-ttu-id="f6ca8-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f6ca8-106">This example requires:</span></span>  
  
-   <span data-ttu-id="f6ca8-107">Nahradit název souboru `"c:\Windows\Media\chimes.wav"` s platným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="f6ca8-107">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
-   <span data-ttu-id="f6ca8-108">(C#) Odkaz na <xref:System.Media?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f6ca8-108">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f6ca8-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f6ca8-109">Robust Programming</span></span>  
 <span data-ttu-id="f6ca8-110">Operace se soubory by měl být uzavřen v rámci příslušné bloky zpracování strukturovaných výjimek.</span><span class="sxs-lookup"><span data-stu-id="f6ca8-110">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>  
  
 <span data-ttu-id="f6ca8-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="f6ca8-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f6ca8-112">Název cesty je poškozený.</span><span class="sxs-lookup"><span data-stu-id="f6ca8-112">The path name is malformed.</span></span> <span data-ttu-id="f6ca8-113">Například obsahuje neplatné znaky nebo je prázdné znaky (<xref:System.ArgumentException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f6ca8-113">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="f6ca8-114">Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f6ca8-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="f6ca8-115">Název cesty je `null` (<xref:System.ArgumentNullException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f6ca8-115">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="f6ca8-116">Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f6ca8-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="f6ca8-117">Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f6ca8-117">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="f6ca8-118">Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException> třídy).</span><span class="sxs-lookup"><span data-stu-id="f6ca8-118">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f6ca8-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6ca8-119">.NET Framework Security</span></span>  
 <span data-ttu-id="f6ca8-120">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="f6ca8-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="f6ca8-121">Například soubor `Form1.vb` nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f6ca8-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="f6ca8-122">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="f6ca8-122">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ca8-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6ca8-123">See also</span></span>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="f6ca8-124">Postupy: Načítání zvuku ve formuláři Windows asynchronně</span><span class="sxs-lookup"><span data-stu-id="f6ca8-124">How to: Load a Sound Asynchronously within a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)

