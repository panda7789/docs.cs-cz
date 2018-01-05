---
title: "Postupy: Přehrávání zvuku z formuláře Windows"
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
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31c9495e22af0e06869d54f02d4ce0e866e28dbb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="99311-102">Postupy: Přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="99311-102">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="99311-103">Tento příklad hraje zvuk, který v dané cestě za běhu.</span><span class="sxs-lookup"><span data-stu-id="99311-103">This example plays a sound at a given path at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99311-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="99311-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="99311-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="99311-105">Compiling the Code</span></span>  
 <span data-ttu-id="99311-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="99311-106">This example requires:</span></span>  
  
-   <span data-ttu-id="99311-107">Nahradit název souboru `"c:\Windows\Media\chimes.wav"` s platný název souboru.</span><span class="sxs-lookup"><span data-stu-id="99311-107">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
-   <span data-ttu-id="99311-108">(C#) Odkaz na <xref:System.Media?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="99311-108">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="99311-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="99311-109">Robust Programming</span></span>  
 <span data-ttu-id="99311-110">Operace se soubory by měl být uzavřen odpovídající strukturovaného zpracování bloky výjimek.</span><span class="sxs-lookup"><span data-stu-id="99311-110">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>  
  
 <span data-ttu-id="99311-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="99311-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="99311-112">Název cesty je chybný.</span><span class="sxs-lookup"><span data-stu-id="99311-112">The path name is malformed.</span></span> <span data-ttu-id="99311-113">Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException> třídy).</span><span class="sxs-lookup"><span data-stu-id="99311-113">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="99311-114">Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).</span><span class="sxs-lookup"><span data-stu-id="99311-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="99311-115">Název cesty je `null` (<xref:System.ArgumentNullException> třídy).</span><span class="sxs-lookup"><span data-stu-id="99311-115">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="99311-116">Cesta je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="99311-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="99311-117">Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třídy).</span><span class="sxs-lookup"><span data-stu-id="99311-117">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="99311-118">Cesta je pouze středník ":" (<xref:System.NotSupportedException> třídy).</span><span class="sxs-lookup"><span data-stu-id="99311-118">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="99311-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="99311-119">.NET Framework Security</span></span>  
 <span data-ttu-id="99311-120">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="99311-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="99311-121">Například soubor `Form1.vb` nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="99311-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="99311-122">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="99311-122">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99311-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="99311-123">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="99311-124">Postupy: Asynchronní načítání zvuku ve formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="99311-124">How to: Load a Sound Asynchronously within a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)  
 
