---
title: "Interoperabilita (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5822f2e4e120f476d925520f0681055f058e3df1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="eb207-102">Interoperabilita (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="eb207-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="eb207-103">Vzájemná funkční spolupráce umožňuje zachovat a využít existující investice v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="eb207-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="eb207-104">Kód, který běží pod kontrolou common language runtime (CLR) se nazývá *spravovaného kódu*, a kód, který je spuštěn mimo modulu CLR se nazývá *nespravovaného kódu*.</span><span class="sxs-lookup"><span data-stu-id="eb207-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="eb207-105">COM, COM +, C++ komponent, součásti ActiveX a Microsoft Win32 API jsou příklady nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="eb207-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="eb207-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umožňuje Interoperabilita s nespravovaným kódem prostřednictvím platformy vyvolání služby, <xref:System.Runtime.InteropServices> obor názvů, interoperabilita C++ a interoperabilita modelů COM (spoluprací COM).</span><span class="sxs-lookup"><span data-stu-id="eb207-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb207-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="eb207-107">In This Section</span></span>  
 [<span data-ttu-id="eb207-108">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="eb207-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="eb207-109">Popisuje metody pro spolupráci mezi C# spravovaný kód a nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="eb207-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="eb207-110">Postupy: přístup k objektům spolupráce sady Office pomocí Visual C# – funkce</span><span class="sxs-lookup"><span data-stu-id="eb207-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="eb207-111">Popisuje funkce, které jsou zavedené v jazyce Visual C# pro usnadnění programování pro Office.</span><span class="sxs-lookup"><span data-stu-id="eb207-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="eb207-112">Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="eb207-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="eb207-113">Popisuje, jak používat indexované vlastnosti pro přístup COM vlastnosti, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="eb207-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="eb207-114">Postupy: použití vyvolání platformy pro přehrání souboru Wave</span><span class="sxs-lookup"><span data-stu-id="eb207-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="eb207-115">Popisuje způsob použití platformy vyvolání služby k přehrání zvukového souboru ve formátu WAV operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="eb207-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="eb207-116">Návod: Programování pro Office</span><span class="sxs-lookup"><span data-stu-id="eb207-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="eb207-117">Ukazuje, jak vytvořit sešit aplikace Excel a Word dokumentu, který obsahuje odkaz na sešitu.</span><span class="sxs-lookup"><span data-stu-id="eb207-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="eb207-118">Ukázka třídy COM</span><span class="sxs-lookup"><span data-stu-id="eb207-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="eb207-119">Ukazuje, jak vystavit třída C# jako objekt COM.</span><span class="sxs-lookup"><span data-stu-id="eb207-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="eb207-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eb207-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eb207-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb207-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="eb207-122">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="eb207-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="eb207-123">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="eb207-123">Interoperating with Unmanaged Code</span></span>](https://msdn.microsoft.com/library/sd10k43k)  
 [<span data-ttu-id="eb207-124">Návod: Programování pro Office</span><span class="sxs-lookup"><span data-stu-id="eb207-124">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
