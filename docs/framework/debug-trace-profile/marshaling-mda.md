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
ms.openlocfilehash: 463c8e42e76a61eb0820c1af72c20d004161ad25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753969"
---
# <a name="marshaling-mda"></a><span data-ttu-id="3794d-102">zařazování MDA</span><span class="sxs-lookup"><span data-stu-id="3794d-102">marshaling MDA</span></span>
<span data-ttu-id="3794d-103">`marshaling` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR nastaví zařazovací informace pro parametr metody nebo pole struktury.</span><span class="sxs-lookup"><span data-stu-id="3794d-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="3794d-104">Toto MDA nefunguje pro sestavení s kompilací JIT.</span><span class="sxs-lookup"><span data-stu-id="3794d-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3794d-105">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="3794d-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="3794d-106">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="3794d-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3794d-107">Výstup</span><span class="sxs-lookup"><span data-stu-id="3794d-107">Output</span></span>  
 <span data-ttu-id="3794d-108">MDA zobrazí typ parametru nebo pole v kontextech spravované a nespravované a struktury nebo metody obsahující typ.</span><span class="sxs-lookup"><span data-stu-id="3794d-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="3794d-109">Následuje příklad výstupu pro pole:</span><span class="sxs-lookup"><span data-stu-id="3794d-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="3794d-110">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="3794d-110">Configuration</span></span>  
 <span data-ttu-id="3794d-111">Konfigurace MDA vám umožní filtrovat ohlášené zařazovací informace na základě zahrnutých pole nebo metoda názvů.</span><span class="sxs-lookup"><span data-stu-id="3794d-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="3794d-112">Následující příklad ukazuje použití `methodFilter`, `fieldFilter`, a `match` prvky zadat filtry.</span><span class="sxs-lookup"><span data-stu-id="3794d-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="3794d-113">Nastavení `name` atribut na hvězdičku (\*) budou odpovídat všechno.</span><span class="sxs-lookup"><span data-stu-id="3794d-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3794d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3794d-114">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="3794d-115">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="3794d-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3794d-116">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="3794d-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
