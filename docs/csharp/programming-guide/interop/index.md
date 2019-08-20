---
title: Interoperabilita C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 896f89304289fd90c10da9aaa7ea15ada35ef8f7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589091"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="e660a-102">Interoperabilita (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e660a-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="e660a-103">Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e660a-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="e660a-104">Kód, který se spouští pod kontrolou modulu CLR (Common Language Runtime), se nazývá *spravovaný kód*a kód, který se spouští mimo modul CLR, se nazývá nespravovaný *kód*.</span><span class="sxs-lookup"><span data-stu-id="e660a-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="e660a-105">Příklady nespravovaného C++ kódu jsou com, com+, komponenty, komponenty ActiveX a rozhraní Microsoft Windows API.</span><span class="sxs-lookup"><span data-stu-id="e660a-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="e660a-106">.NET Framework umožňuje vzájemnou funkční spolupráci s nespravovaným kódem prostřednictvím služeb <xref:System.Runtime.InteropServices> vyvolání platformy C++ , oboru názvů, interoperability a interoperability modelu COM (komunikace s objekty com).</span><span class="sxs-lookup"><span data-stu-id="e660a-106">The .NET Framework enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e660a-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e660a-107">In This Section</span></span>  
 [<span data-ttu-id="e660a-108">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="e660a-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="e660a-109">Popisuje metody vzájemné spolupráce mezi C# spravovaným kódem a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="e660a-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="e660a-110">Postupy: Přístup k objektům Interop Office pomocí C# vizuálních funkcí</span><span class="sxs-lookup"><span data-stu-id="e660a-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="e660a-111">Popisuje funkce, které jsou představené C# ve vizuálu pro usnadnění programování pro Office.</span><span class="sxs-lookup"><span data-stu-id="e660a-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="e660a-112">Postupy: Použití indexovaných vlastností v programování zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="e660a-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="e660a-113">Popisuje způsob použití indexovaných vlastností pro přístup k vlastnostem modelu COM, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="e660a-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="e660a-114">Postupy: Použít vyvolání platformy k přehrání souboru Wave</span><span class="sxs-lookup"><span data-stu-id="e660a-114">How to: Use Platform Invoke to Play a Wave File</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="e660a-115">Popisuje způsob použití služeb vyvolání platformy k přehrání zvukového souboru. wav v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e660a-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="e660a-116">Návod: Programování pro Office</span><span class="sxs-lookup"><span data-stu-id="e660a-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="e660a-117">Ukazuje, jak vytvořit excelový sešit a wordový dokument, který obsahuje odkaz na sešit.</span><span class="sxs-lookup"><span data-stu-id="e660a-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="e660a-118">Ukázka třídy COM</span><span class="sxs-lookup"><span data-stu-id="e660a-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="e660a-119">Ukazuje, jak vystavit C# třídu jako objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e660a-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e660a-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e660a-120">C# Language Specification</span></span>  

<span data-ttu-id="e660a-121">Další informace najdete v tématu [základní koncepty](~/_csharplang/spec/unsafe-code.md) ve [ C# specifikaci jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e660a-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="e660a-122">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e660a-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e660a-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e660a-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e660a-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e660a-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e660a-125">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="e660a-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="e660a-126">Návod: Programování pro Office</span><span class="sxs-lookup"><span data-stu-id="e660a-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
