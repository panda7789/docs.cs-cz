---
title: "zařazování MDA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83b621f78e3ba4641540f6125ed14d600cc292d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-mda"></a><span data-ttu-id="8e05f-102">zařazování MDA</span><span class="sxs-lookup"><span data-stu-id="8e05f-102">marshaling MDA</span></span>
<span data-ttu-id="8e05f-103">`marshaling` Pomocník spravovaného ladění (MDA) se aktivuje, když modul CLR nastaví zařazování informace o parametru metody nebo pole do struktury.</span><span class="sxs-lookup"><span data-stu-id="8e05f-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="8e05f-104">Tato MDA nefunguje pro kompilována sestavení.</span><span class="sxs-lookup"><span data-stu-id="8e05f-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8e05f-105">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="8e05f-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="8e05f-106">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="8e05f-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8e05f-107">Výstup</span><span class="sxs-lookup"><span data-stu-id="8e05f-107">Output</span></span>  
 <span data-ttu-id="8e05f-108">MDA zobrazí typ parametru nebo pole v kontexty spravovanými a nespravovanými a struktura nebo metoda obsahující typ.</span><span class="sxs-lookup"><span data-stu-id="8e05f-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="8e05f-109">Následuje příklad výstupu pro pole:</span><span class="sxs-lookup"><span data-stu-id="8e05f-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="8e05f-110">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8e05f-110">Configuration</span></span>  
 <span data-ttu-id="8e05f-111">Konfigurace (mda) vám umožní filtrovat hlášených zařazování informací na základě související se situací pole nebo metoda názvů.</span><span class="sxs-lookup"><span data-stu-id="8e05f-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="8e05f-112">Následující příklad ukazuje použití `methodFilter`, `fieldFilter`, a `match` prvky zadat filtry.</span><span class="sxs-lookup"><span data-stu-id="8e05f-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="8e05f-113">Nastavení `name` atribut na hvězdičku (*) bude odpovídat vše.</span><span class="sxs-lookup"><span data-stu-id="8e05f-113">Setting the `name` attribute to an asterisk (*) will match everything.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e05f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e05f-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="8e05f-115">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="8e05f-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="8e05f-116">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="8e05f-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
