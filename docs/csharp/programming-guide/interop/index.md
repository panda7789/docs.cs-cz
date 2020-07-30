---
title: Interoperabilita – Průvodce programováním v C#
description: Interoperabilita podporuje nespravovaný kód vedle kódu, který běží v modulu CLR (Common Language Runtime). Pomocí těchto zdrojů můžete pochopit možnosti spolupráce.
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: d85eb51107d50e023270fcbe1ef6e08a7788ae78
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302968"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="e4043-104">Interoperabilita (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e4043-104">Interoperability (C# Programming Guide)</span></span>

<span data-ttu-id="e4043-105">Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e4043-105">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="e4043-106">Kód, který se spouští pod kontrolou modulu CLR (Common Language Runtime), se nazývá *spravovaný kód*a kód, který se spouští mimo modul CLR, se nazývá *nespravovaný kód*.</span><span class="sxs-lookup"><span data-stu-id="e4043-106">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="e4043-107">Příklady nespravovaného kódu jsou komponenty COM, COM+, C++, komponenty ActiveX a rozhraní Microsoft Windows API.</span><span class="sxs-lookup"><span data-stu-id="e4043-107">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
<span data-ttu-id="e4043-108">.NET umožňuje vzájemnou funkční spolupráci s nespravovaným kódem prostřednictvím služeb vyvolání platformy, <xref:System.Runtime.InteropServices> oboru názvů, interoperability C++ a interoperability com (interoperabilita com).</span><span class="sxs-lookup"><span data-stu-id="e4043-108">.NET enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4043-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e4043-109">In This Section</span></span>  
 [<span data-ttu-id="e4043-110">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="e4043-110">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="e4043-111">Popisuje metody vzájemné spolupráce mezi spravovaným kódem jazyka C# a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="e4043-111">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="e4043-112">Jak získat přístup k objektům interoperability Office pomocí funkcí jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e4043-112">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="e4043-113">Popisuje funkce, které jsou představeny v jazyce Visual C# pro usnadnění programování v systému Office.</span><span class="sxs-lookup"><span data-stu-id="e4043-113">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="e4043-114">Jak použít indexované vlastnosti při programování interoperability COM</span><span class="sxs-lookup"><span data-stu-id="e4043-114">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="e4043-115">Popisuje způsob použití indexovaných vlastností pro přístup k vlastnostem modelu COM, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="e4043-115">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="e4043-116">Jak použít vyvolání platformy k přehrání souboru WAV</span><span class="sxs-lookup"><span data-stu-id="e4043-116">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="e4043-117">Popisuje způsob použití služeb vyvolání platformy k přehrání zvukového souboru. wav v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e4043-117">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="e4043-118">Návod: programování pro Office</span><span class="sxs-lookup"><span data-stu-id="e4043-118">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="e4043-119">Ukazuje, jak vytvořit excelový sešit a wordový dokument, který obsahuje odkaz na sešit.</span><span class="sxs-lookup"><span data-stu-id="e4043-119">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="e4043-120">Ukázka třídy COM</span><span class="sxs-lookup"><span data-stu-id="e4043-120">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="e4043-121">Ukazuje, jak vystavit třídu jazyka C# jako objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e4043-121">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e4043-122">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e4043-122">C# Language Specification</span></span>  

<span data-ttu-id="e4043-123">Další informace najdete v tématu [základní koncepty](~/_csharplang/spec/unsafe-code.md) [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="e4043-123">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="e4043-124">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e4043-124">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e4043-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4043-125">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e4043-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e4043-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e4043-127">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="e4043-127">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="e4043-128">Návod: programování pro Office</span><span class="sxs-lookup"><span data-stu-id="e4043-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
