---
title: Interoperabilita C# – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712049"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="08bb5-102">Interoperabilita (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="08bb5-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="08bb5-103">Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="08bb5-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="08bb5-104">Kód, který se spouští pod kontrolou modulu CLR (Common Language Runtime), se nazývá *spravovaný kód*a kód, který se spouští mimo modul CLR, se nazývá *nespravovaný kód*.</span><span class="sxs-lookup"><span data-stu-id="08bb5-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="08bb5-105">Příklady nespravovaného C++ kódu jsou com, com+, komponenty, komponenty ActiveX a rozhraní Microsoft Windows API.</span><span class="sxs-lookup"><span data-stu-id="08bb5-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="08bb5-106">.NET Framework umožňuje vzájemnou funkční spolupráci s nespravovaným kódem prostřednictvím služeb vyvolání platformy, C++ <xref:System.Runtime.InteropServices> oboru názvů, interoperability a interoperability com (interoperabilita com).</span><span class="sxs-lookup"><span data-stu-id="08bb5-106">The .NET Framework enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08bb5-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="08bb5-107">In This Section</span></span>  
 [<span data-ttu-id="08bb5-108">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="08bb5-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="08bb5-109">Popisuje metody vzájemné spolupráce mezi C# spravovaným kódem a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="08bb5-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="08bb5-110">Přístup k objektům Interop sady Office pomocí C# funkcí</span><span class="sxs-lookup"><span data-stu-id="08bb5-110">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="08bb5-111">Popisuje funkce, které jsou představené C# ve vizuálu pro usnadnění programování pro Office.</span><span class="sxs-lookup"><span data-stu-id="08bb5-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="08bb5-112">Použití indexovaných vlastností v programování zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="08bb5-112">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="08bb5-113">Popisuje způsob použití indexovaných vlastností pro přístup k vlastnostem modelu COM, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="08bb5-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="08bb5-114">Jak použít vyvolání platformy k přehrání souboru WAV</span><span class="sxs-lookup"><span data-stu-id="08bb5-114">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="08bb5-115">Popisuje způsob použití služeb vyvolání platformy k přehrání zvukového souboru. wav v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="08bb5-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="08bb5-116">Návod: programování pro Office</span><span class="sxs-lookup"><span data-stu-id="08bb5-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="08bb5-117">Ukazuje, jak vytvořit excelový sešit a wordový dokument, který obsahuje odkaz na sešit.</span><span class="sxs-lookup"><span data-stu-id="08bb5-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="08bb5-118">Ukázka třídy COM</span><span class="sxs-lookup"><span data-stu-id="08bb5-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="08bb5-119">Ukazuje, jak vystavit C# třídu jako objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="08bb5-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="08bb5-120">C# – jazyková specifikace</span><span class="sxs-lookup"><span data-stu-id="08bb5-120">C# Language Specification</span></span>  

<span data-ttu-id="08bb5-121">Další informace najdete v tématu [základní koncepty](~/_csharplang/spec/unsafe-code.md) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="08bb5-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="08bb5-122">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="08bb5-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="08bb5-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08bb5-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="08bb5-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="08bb5-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="08bb5-125">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="08bb5-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="08bb5-126">Návod: programování pro Office</span><span class="sxs-lookup"><span data-stu-id="08bb5-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
