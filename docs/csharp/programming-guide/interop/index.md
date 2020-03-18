---
title: Průvodce programováním v jazyce Interoperability – C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712049"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="e81ac-102">Interoperabilita (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e81ac-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="e81ac-103">Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e81ac-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="e81ac-104">Kód, který běží pod kontrolou clr (COMMON Language Runtime), se nazývá *spravovaný kód*a kód, který běží mimo CLR, se nazývá *nespravovaný kód*.</span><span class="sxs-lookup"><span data-stu-id="e81ac-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="e81ac-105">Com, COM+, C++ komponenty, komponenty ActiveX a rozhraní Microsoft Windows API jsou příklady nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e81ac-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="e81ac-106">Rozhraní .NET Framework umožňuje interoperabilitu s <xref:System.Runtime.InteropServices> nespravovaným kódem prostřednictvím služeb vyvolání platformy, oboru názvů, interoperability jazyka C++ a interoperability modelu COM (interop modelu COM).</span><span class="sxs-lookup"><span data-stu-id="e81ac-106">The .NET Framework enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e81ac-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e81ac-107">In This Section</span></span>  
 [<span data-ttu-id="e81ac-108">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="e81ac-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="e81ac-109">Popisuje metody pro vzájemné propojení mezi spravovaným kódem jazyka C# a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="e81ac-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="e81ac-110">Jak získat přístup k objektům interoperability Office pomocí funkcí jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e81ac-110">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="e81ac-111">Popisuje funkce, které jsou zavedeny v jazyce Visual C# pro usnadnění programování sady Office.</span><span class="sxs-lookup"><span data-stu-id="e81ac-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="e81ac-112">Jak použít indexované vlastnosti při programování interoperability COM</span><span class="sxs-lookup"><span data-stu-id="e81ac-112">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="e81ac-113">Popisuje použití indexovaných vlastností pro přístup k vlastnostem com, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="e81ac-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="e81ac-114">Jak použít vyvolání platformy k přehrání souboru WAV</span><span class="sxs-lookup"><span data-stu-id="e81ac-114">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="e81ac-115">Popisuje způsob, jak pomocí služby vyvolání platformy přehrát zvukový soubor WAV v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e81ac-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="e81ac-116">Návod: Programování v Office</span><span class="sxs-lookup"><span data-stu-id="e81ac-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="e81ac-117">Ukazuje, jak vytvořit excelový sešit a wordový dokument obsahující odkaz na sešit.</span><span class="sxs-lookup"><span data-stu-id="e81ac-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="e81ac-118">Ukázka třídy COM</span><span class="sxs-lookup"><span data-stu-id="e81ac-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="e81ac-119">Ukazuje, jak vystavit třídu C# jako objekt COM.</span><span class="sxs-lookup"><span data-stu-id="e81ac-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e81ac-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e81ac-120">C# Language Specification</span></span>  

<span data-ttu-id="e81ac-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="e81ac-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="e81ac-122">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e81ac-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e81ac-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e81ac-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e81ac-124">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e81ac-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e81ac-125">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="e81ac-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="e81ac-126">Návod: Programování v Office</span><span class="sxs-lookup"><span data-stu-id="e81ac-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
