---
title: zařazování MDA
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: f7bb630d3a1e832cf6bf083ce4cf603034248ceb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217324"
---
# <a name="marshaling-mda"></a>zařazování MDA
Když CLR nastaví zařazovací informace pro parametr metody nebo pole struktury, aktivuje se Pomocník s `marshaling`em spravovaného ladění (MDA). Tento MDA nefunguje pro sestavení kompilovaná JIT.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 MDA zobrazuje typ parametru nebo pole ve spravovaných a nespravovaných kontextech a strukturu nebo metodu obsahující typ.  Následuje příklad výstupu pole:  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a>Konfigurace  
 Konfigurace MDA umožňuje filtrovat hlášené informace o zařazování na základě názvu pole nebo metody.  Následující příklad ukazuje použití prvků `methodFilter`, `fieldFilter`a `match` k určení filtrů.  Nastavením atributu `name` na hvězdičku (\*) se bude shodovat vše.  
  
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

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
