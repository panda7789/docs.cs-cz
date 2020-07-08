---
title: zařazování MDA
description: Projděte si průvodce zařazování spravovaného ladění (MDA), který je vyvolán, pokud CLR nastaví zařazovací informace pro parametr metody nebo pole struktury.
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: 77811c526d1770b91b14aa1199dfc7b3177e6c59
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051152"
---
# <a name="marshaling-mda"></a><span data-ttu-id="32cee-103">zařazování MDA</span><span class="sxs-lookup"><span data-stu-id="32cee-103">marshaling MDA</span></span>
<span data-ttu-id="32cee-104">`marshaling`Pokud CLR nastaví zařazovací informace pro parametr metody nebo pole struktury, je aktivován pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="32cee-104">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="32cee-105">Tento MDA nefunguje pro sestavení kompilovaná JIT.</span><span class="sxs-lookup"><span data-stu-id="32cee-105">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="32cee-106">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="32cee-106">Effect on the Runtime</span></span>  
 <span data-ttu-id="32cee-107">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="32cee-107">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="32cee-108">Výstup</span><span class="sxs-lookup"><span data-stu-id="32cee-108">Output</span></span>  
 <span data-ttu-id="32cee-109">MDA zobrazuje typ parametru nebo pole ve spravovaných a nespravovaných kontextech a strukturu nebo metodu obsahující typ.</span><span class="sxs-lookup"><span data-stu-id="32cee-109">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="32cee-110">Následuje příklad výstupu pole:</span><span class="sxs-lookup"><span data-stu-id="32cee-110">The following is an example of the output for a field:</span></span>  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="32cee-111">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="32cee-111">Configuration</span></span>  
 <span data-ttu-id="32cee-112">Konfigurace MDA umožňuje filtrovat hlášené informace o zařazování na základě názvu pole nebo metody.</span><span class="sxs-lookup"><span data-stu-id="32cee-112">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="32cee-113">Následující příklad ukazuje použití `methodFilter` `fieldFilter` prvků, a `match` k určení filtrů.</span><span class="sxs-lookup"><span data-stu-id="32cee-113">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="32cee-114">Nastavení `name` atributu na hvězdičku ( \* ) bude odpovídat všem.</span><span class="sxs-lookup"><span data-stu-id="32cee-114">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32cee-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="32cee-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="32cee-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="32cee-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="32cee-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="32cee-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
