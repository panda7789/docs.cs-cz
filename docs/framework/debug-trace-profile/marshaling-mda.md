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
ms.openlocfilehash: 1e1583ba8ecfa461958f96bea6cb2b9d3313349b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967286"
---
# <a name="marshaling-mda"></a><span data-ttu-id="491eb-102">zařazování MDA</span><span class="sxs-lookup"><span data-stu-id="491eb-102">marshaling MDA</span></span>
<span data-ttu-id="491eb-103">Pokud CLR nastaví zařazovací informace pro parametr metody nebo pole struktury, je aktivován pomocník spravovanéholadění(MDA).`marshaling`</span><span class="sxs-lookup"><span data-stu-id="491eb-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="491eb-104">Tento MDA nefunguje pro sestavení kompilovaná JIT.</span><span class="sxs-lookup"><span data-stu-id="491eb-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="491eb-105">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="491eb-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="491eb-106">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="491eb-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="491eb-107">Výstup</span><span class="sxs-lookup"><span data-stu-id="491eb-107">Output</span></span>  
 <span data-ttu-id="491eb-108">MDA zobrazuje typ parametru nebo pole ve spravovaných a nespravovaných kontextech a strukturu nebo metodu obsahující typ.</span><span class="sxs-lookup"><span data-stu-id="491eb-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="491eb-109">Následuje příklad výstupu pole:</span><span class="sxs-lookup"><span data-stu-id="491eb-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="491eb-110">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="491eb-110">Configuration</span></span>  
 <span data-ttu-id="491eb-111">Konfigurace MDA umožňuje filtrovat hlášené informace o zařazování na základě názvu pole nebo metody.</span><span class="sxs-lookup"><span data-stu-id="491eb-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="491eb-112">Následující příklad ukazuje použití `methodFilter`prvků, `fieldFilter`a `match` k určení filtrů.</span><span class="sxs-lookup"><span data-stu-id="491eb-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="491eb-113">Nastavení atributu na hvězdičku (\*) bude odpovídat všem. `name`</span><span class="sxs-lookup"><span data-stu-id="491eb-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="491eb-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="491eb-114">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="491eb-115">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="491eb-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="491eb-116">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="491eb-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
