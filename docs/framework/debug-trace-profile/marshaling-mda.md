---
title: zařazování MDA
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 164c7a6e4411d7ff3e66643c6f012fdba790ef49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386675"
---
# <a name="marshaling-mda"></a><span data-ttu-id="b93d3-102">zařazování MDA</span><span class="sxs-lookup"><span data-stu-id="b93d3-102">marshaling MDA</span></span>
<span data-ttu-id="b93d3-103">`marshaling` Pomocník spravovaného ladění (MDA) se aktivuje, když modul CLR nastaví zařazování informace o parametru metody nebo pole do struktury.</span><span class="sxs-lookup"><span data-stu-id="b93d3-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="b93d3-104">Tato MDA nefunguje pro kompilována sestavení.</span><span class="sxs-lookup"><span data-stu-id="b93d3-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b93d3-105">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="b93d3-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="b93d3-106">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b93d3-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b93d3-107">Výstup</span><span class="sxs-lookup"><span data-stu-id="b93d3-107">Output</span></span>  
 <span data-ttu-id="b93d3-108">MDA zobrazí typ parametru nebo pole v kontexty spravovanými a nespravovanými a struktura nebo metoda obsahující typ.</span><span class="sxs-lookup"><span data-stu-id="b93d3-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="b93d3-109">Následuje příklad výstupu pro pole:</span><span class="sxs-lookup"><span data-stu-id="b93d3-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="b93d3-110">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b93d3-110">Configuration</span></span>  
 <span data-ttu-id="b93d3-111">Konfigurace (mda) vám umožní filtrovat hlášených zařazování informací na základě související se situací pole nebo metoda názvů.</span><span class="sxs-lookup"><span data-stu-id="b93d3-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="b93d3-112">Následující příklad ukazuje použití `methodFilter`, `fieldFilter`, a `match` prvky zadat filtry.</span><span class="sxs-lookup"><span data-stu-id="b93d3-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="b93d3-113">Nastavení `name` atribut na hvězdičku (\*) bude odpovídat vše.</span><span class="sxs-lookup"><span data-stu-id="b93d3-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b93d3-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b93d3-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="b93d3-115">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="b93d3-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="b93d3-116">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="b93d3-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
