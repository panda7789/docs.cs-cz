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
ms.openlocfilehash: 853d0f78b4f6dba2dc84109270f79f4b010c27b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533517"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="c6078-102">Postupy: Přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="c6078-102">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="c6078-103">Tento příklad hraje zvuk, který v dané cestě za běhu.</span><span class="sxs-lookup"><span data-stu-id="c6078-103">This example plays a sound at a given path at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6078-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6078-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="c6078-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c6078-105">Compiling the Code</span></span>  
 <span data-ttu-id="c6078-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c6078-106">This example requires:</span></span>  
  
-   <span data-ttu-id="c6078-107">Nahradit název souboru `"c:\Windows\Media\chimes.wav"` s platný název souboru.</span><span class="sxs-lookup"><span data-stu-id="c6078-107">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
-   <span data-ttu-id="c6078-108">(C#) Odkaz na <xref:System.Media?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c6078-108">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c6078-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c6078-109">Robust Programming</span></span>  
 <span data-ttu-id="c6078-110">Operace se soubory by měl být uzavřen odpovídající strukturovaného zpracování bloky výjimek.</span><span class="sxs-lookup"><span data-stu-id="c6078-110">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>  
  
 <span data-ttu-id="c6078-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="c6078-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c6078-112">Název cesty je chybný.</span><span class="sxs-lookup"><span data-stu-id="c6078-112">The path name is malformed.</span></span> <span data-ttu-id="c6078-113">Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException> třídy).</span><span class="sxs-lookup"><span data-stu-id="c6078-113">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="c6078-114">Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).</span><span class="sxs-lookup"><span data-stu-id="c6078-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="c6078-115">Název cesty je `null` (<xref:System.ArgumentNullException> třídy).</span><span class="sxs-lookup"><span data-stu-id="c6078-115">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="c6078-116">Cesta je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="c6078-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="c6078-117">Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třídy).</span><span class="sxs-lookup"><span data-stu-id="c6078-117">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="c6078-118">Cesta je pouze středník ":" (<xref:System.NotSupportedException> třídy).</span><span class="sxs-lookup"><span data-stu-id="c6078-118">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c6078-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c6078-119">.NET Framework Security</span></span>  
 <span data-ttu-id="c6078-120">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="c6078-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="c6078-121">Například soubor `Form1.vb` nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c6078-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="c6078-122">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="c6078-122">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6078-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6078-123">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="c6078-124">Postupy: Asynchronní načítání zvuku ve formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6078-124">How to: Load a Sound Asynchronously within a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)  
 
