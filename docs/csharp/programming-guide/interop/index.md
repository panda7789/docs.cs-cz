---
title: Interoperabilita (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: dc68a2a9c21f6fdb9b531bd07428325ac22ebfb6
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "50980645"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="5426e-102">Interoperabilita (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5426e-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="5426e-103">Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5426e-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="5426e-104">Je volána kód, který běží v rámci ovládacího prvku modulu common language runtime (CLR) *spravovaného kódu*, a je volána kód, který běží mimo rámec platformy CLR *nespravovaný kód*.</span><span class="sxs-lookup"><span data-stu-id="5426e-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="5426e-105">COM, modelu COM +, komponenty C++, součásti ActiveX a rozhraní Microsoft Win32 API jsou příkladem nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5426e-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="5426e-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umožňuje vzájemná funkční spolupráce s nespravovaným kódem prostřednictvím platformy vyvolat služby, <xref:System.Runtime.InteropServices> obor názvů, vzájemná funkční spolupráce jazyka C++ a vzájemná funkční spolupráce modelu COM (komunikace s objekty COM).</span><span class="sxs-lookup"><span data-stu-id="5426e-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5426e-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5426e-107">In This Section</span></span>  
 [<span data-ttu-id="5426e-108">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="5426e-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="5426e-109">Popisuje metody pro spolupráci mezi kód jazyka C# spravovaného a nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5426e-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="5426e-110">Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C#</span><span class="sxs-lookup"><span data-stu-id="5426e-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="5426e-111">Popisuje funkce, které se zavedly v jazyce Visual C# k usnadnění programování pro Office.</span><span class="sxs-lookup"><span data-stu-id="5426e-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="5426e-112">Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="5426e-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="5426e-113">Popisuje, jak používat indexované vlastnosti pro přístup k vlastnostem modelu COM, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="5426e-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="5426e-114">Postupy: Použití vyvolání platformy pro přehrání souboru wave</span><span class="sxs-lookup"><span data-stu-id="5426e-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="5426e-115">Popisuje, jak používat platformu vyvolání služby k přehrání zvukového souboru WAV v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5426e-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="5426e-116">Postupy: Programování pro systém Office</span><span class="sxs-lookup"><span data-stu-id="5426e-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="5426e-117">Ukazuje, jak vytvořit Excelový sešit a dokument aplikace Word, který obsahuje odkaz na sešit.</span><span class="sxs-lookup"><span data-stu-id="5426e-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="5426e-118">Ukázka třídy COM</span><span class="sxs-lookup"><span data-stu-id="5426e-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="5426e-119">Ukazuje, jak vystavit třída jazyka C# jako objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5426e-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="5426e-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5426e-120">C# Language Specification</span></span>  

<span data-ttu-id="5426e-121">Další informace najdete v tématu [základní koncepty](~/_csharplang/spec/unsafe-code.md) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="5426e-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="5426e-122">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="5426e-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5426e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5426e-123">See Also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="5426e-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5426e-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5426e-125">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="5426e-125">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
- [<span data-ttu-id="5426e-126">Postupy: Programování pro systém Office</span><span class="sxs-lookup"><span data-stu-id="5426e-126">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
