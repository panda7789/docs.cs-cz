---
title: Interoperabilita (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: e854c51bd80809b92bb538475a407422b2eba7c0
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925633"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="0a79b-102">Interoperabilita (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="0a79b-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="0a79b-103">Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="0a79b-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="0a79b-104">Je volána kód, který běží v rámci ovládacího prvku modulu common language runtime (CLR) *spravovaného kódu*, a je volána kód, který běží mimo rámec platformy CLR *nespravovaný kód*.</span><span class="sxs-lookup"><span data-stu-id="0a79b-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="0a79b-105">COM, modelu COM +, komponenty C++, součásti ActiveX a rozhraní Microsoft Win32 API jsou příkladem nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="0a79b-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="0a79b-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umožňuje vzájemná funkční spolupráce s nespravovaným kódem prostřednictvím platformy vyvolat služby, <xref:System.Runtime.InteropServices> obor názvů, vzájemná funkční spolupráce jazyka C++ a vzájemná funkční spolupráce modelu COM (komunikace s objekty COM).</span><span class="sxs-lookup"><span data-stu-id="0a79b-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a79b-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0a79b-107">In This Section</span></span>  
 [<span data-ttu-id="0a79b-108">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="0a79b-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="0a79b-109">Popisuje metody pro spolupráci mezi kód jazyka C# spravovaného a nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="0a79b-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="0a79b-110">Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C#</span><span class="sxs-lookup"><span data-stu-id="0a79b-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="0a79b-111">Popisuje funkce, které se zavedly v jazyce Visual C# k usnadnění programování pro Office.</span><span class="sxs-lookup"><span data-stu-id="0a79b-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="0a79b-112">Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="0a79b-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="0a79b-113">Popisuje, jak používat indexované vlastnosti pro přístup k vlastnostem modelu COM, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="0a79b-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="0a79b-114">Postupy: Použití vyvolání platformy pro přehrání souboru wave</span><span class="sxs-lookup"><span data-stu-id="0a79b-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="0a79b-115">Popisuje, jak používat platformu vyvolání služby k přehrání zvukového souboru WAV v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0a79b-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="0a79b-116">Postupy: Programování pro systém Office</span><span class="sxs-lookup"><span data-stu-id="0a79b-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="0a79b-117">Ukazuje, jak vytvořit Excelový sešit a dokument aplikace Word, který obsahuje odkaz na sešit.</span><span class="sxs-lookup"><span data-stu-id="0a79b-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="0a79b-118">Ukázka třídy COM</span><span class="sxs-lookup"><span data-stu-id="0a79b-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="0a79b-119">Ukazuje, jak vystavit třída jazyka C# jako objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0a79b-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0a79b-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0a79b-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a79b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a79b-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="0a79b-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0a79b-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0a79b-123">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="0a79b-123">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="0a79b-124">Postupy: Programování pro systém Office</span><span class="sxs-lookup"><span data-stu-id="0a79b-124">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
