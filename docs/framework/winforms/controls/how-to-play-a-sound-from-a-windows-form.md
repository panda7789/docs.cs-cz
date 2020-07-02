---
title: 'Postupy: Přehrávání zvuku z formuláře Windows'
description: Přečtěte si, jak přehrát zvuk z formuláře Windows v dané cestě za běhu. Přečtěte si také informace o kompilování kódu a rozhraní .NET Security Framework.
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
ms.openlocfilehash: beb17d994e224f41b2b590ecb1401988cdad314d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613745"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="ccca7-104">Postupy: Přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="ccca7-104">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="ccca7-105">Tento příklad hraje zvuk v dané cestě v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ccca7-105">This example plays a sound at a given path at run time.</span></span>

## <a name="example"></a><span data-ttu-id="ccca7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccca7-106">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="ccca7-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ccca7-107">Compiling the Code</span></span>
 <span data-ttu-id="ccca7-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ccca7-108">This example requires:</span></span>

- <span data-ttu-id="ccca7-109">Název souboru nahradíte `"c:\Windows\Media\chimes.wav"` platným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="ccca7-109">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>

- <span data-ttu-id="ccca7-110">Jazyk Odkaz na <xref:System.Media?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ccca7-110">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="ccca7-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ccca7-111">Robust Programming</span></span>
 <span data-ttu-id="ccca7-112">Operace se soubory by měly být uzavřeny v odpovídajících strukturovaných blocích zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="ccca7-112">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>

 <span data-ttu-id="ccca7-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="ccca7-113">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="ccca7-114">Název cesty je poškozen.</span><span class="sxs-lookup"><span data-stu-id="ccca7-114">The path name is malformed.</span></span> <span data-ttu-id="ccca7-115">Například obsahuje neplatné znaky nebo je pouze mezera ( <xref:System.ArgumentException> třída).</span><span class="sxs-lookup"><span data-stu-id="ccca7-115">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>

- <span data-ttu-id="ccca7-116">Cesta je jen pro čtení ( <xref:System.IO.IOException> třída).</span><span class="sxs-lookup"><span data-stu-id="ccca7-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>

- <span data-ttu-id="ccca7-117">Název cesty je `null` ( <xref:System.ArgumentNullException> Class).</span><span class="sxs-lookup"><span data-stu-id="ccca7-117">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>

- <span data-ttu-id="ccca7-118">Název cesty je příliš dlouhý ( <xref:System.IO.PathTooLongException> třída).</span><span class="sxs-lookup"><span data-stu-id="ccca7-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>

- <span data-ttu-id="ccca7-119">Cesta je neplatná ( <xref:System.IO.DirectoryNotFoundException> třída).</span><span class="sxs-lookup"><span data-stu-id="ccca7-119">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>

- <span data-ttu-id="ccca7-120">Cesta je pouze dvojtečka, ":" ( <xref:System.NotSupportedException> třída).</span><span class="sxs-lookup"><span data-stu-id="ccca7-120">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="ccca7-121">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ccca7-121">.NET Framework Security</span></span>
 <span data-ttu-id="ccca7-122">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="ccca7-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="ccca7-123">Soubor nemůže `Form1.vb` být například Visual Basic zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="ccca7-123">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="ccca7-124">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="ccca7-124">Verify all inputs before using the data in your application.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccca7-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccca7-125">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="ccca7-126">Postupy: Asynchronní načítání zvuku ve formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ccca7-126">How to: Load a Sound Asynchronously within a Windows Form</span></span>](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
