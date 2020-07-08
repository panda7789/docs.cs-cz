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
# <a name="marshaling-mda"></a>zařazování MDA
`marshaling`Pokud CLR nastaví zařazovací informace pro parametr metody nebo pole struktury, je aktivován pomocník spravovaného ladění (MDA). Tento MDA nefunguje pro sestavení kompilovaná JIT.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 MDA zobrazuje typ parametru nebo pole ve spravovaných a nespravovaných kontextech a strukturu nebo metodu obsahující typ.  Následuje příklad výstupu pole:  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a>Konfigurace  
 Konfigurace MDA umožňuje filtrovat hlášené informace o zařazování na základě názvu pole nebo metody.  Následující příklad ukazuje použití `methodFilter` `fieldFilter` prvků, a `match` k určení filtrů.  Nastavení `name` atributu na hvězdičku ( \* ) bude odpovídat všem.  
  
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
