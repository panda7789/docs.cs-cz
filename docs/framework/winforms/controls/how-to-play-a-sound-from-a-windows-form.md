---
title: 'Postupy: Přehrávání zvuku z formuláře Windows Forms'
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
ms.openlocfilehash: 68a68f05b847877641132e540995f6b14bb6e065
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015804"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="69085-102">Postupy: Přehrávání zvuku z formuláře Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69085-102">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="69085-103">Tento příklad hraje zvuk v dané cestě v době běhu.</span><span class="sxs-lookup"><span data-stu-id="69085-103">This example plays a sound at a given path at run time.</span></span>

## <a name="example"></a><span data-ttu-id="69085-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="69085-104">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="69085-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="69085-105">Compiling the Code</span></span>
 <span data-ttu-id="69085-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="69085-106">This example requires:</span></span>

- <span data-ttu-id="69085-107">Název `"c:\Windows\Media\chimes.wav"` souboru nahradíte platným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="69085-107">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>

- <span data-ttu-id="69085-108">(C#) Odkaz na <xref:System.Media?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="69085-108">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="69085-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="69085-109">Robust Programming</span></span>
 <span data-ttu-id="69085-110">Operace se soubory by měly být uzavřeny v odpovídajících strukturovaných blocích zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="69085-110">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>

 <span data-ttu-id="69085-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="69085-111">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="69085-112">Název cesty je poškozen.</span><span class="sxs-lookup"><span data-stu-id="69085-112">The path name is malformed.</span></span> <span data-ttu-id="69085-113">Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException> třída).</span><span class="sxs-lookup"><span data-stu-id="69085-113">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>

- <span data-ttu-id="69085-114">Cesta je jen pro čtení (<xref:System.IO.IOException> třída).</span><span class="sxs-lookup"><span data-stu-id="69085-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>

- <span data-ttu-id="69085-115">Název cesty je `null` (<xref:System.ArgumentNullException> Class).</span><span class="sxs-lookup"><span data-stu-id="69085-115">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>

- <span data-ttu-id="69085-116">Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException> třída).</span><span class="sxs-lookup"><span data-stu-id="69085-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>

- <span data-ttu-id="69085-117">Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třída).</span><span class="sxs-lookup"><span data-stu-id="69085-117">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>

- <span data-ttu-id="69085-118">Cesta je pouze dvojtečka, ":" (<xref:System.NotSupportedException> třída).</span><span class="sxs-lookup"><span data-stu-id="69085-118">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="69085-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="69085-119">.NET Framework Security</span></span>
 <span data-ttu-id="69085-120">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="69085-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="69085-121">Soubor `Form1.vb` nemůže být například Visual Basic zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="69085-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="69085-122">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="69085-122">Verify all inputs before using the data in your application.</span></span>

## <a name="see-also"></a><span data-ttu-id="69085-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69085-123">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="69085-124">Postupy: Asynchronní načítání zvuku ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="69085-124">How to: Load a Sound Asynchronously within a Windows Form</span></span>](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
