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
# <a name="marshaling-mda"></a>zařazování MDA
`marshaling` Pomocník spravovaného ladění (MDA) se aktivuje, když modul CLR nastaví zařazování informace o parametru metody nebo pole do struktury. Tato MDA nefunguje pro kompilována sestavení.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 MDA zobrazí typ parametru nebo pole v kontexty spravovanými a nespravovanými a struktura nebo metoda obsahující typ.  Následuje příklad výstupu pro pole:  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a>Konfigurace  
 Konfigurace (mda) vám umožní filtrovat hlášených zařazování informací na základě související se situací pole nebo metoda názvů.  Následující příklad ukazuje použití `methodFilter`, `fieldFilter`, a `match` prvky zadat filtry.  Nastavení `name` atribut na hvězdičku (*) bude odpovídat vše.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
