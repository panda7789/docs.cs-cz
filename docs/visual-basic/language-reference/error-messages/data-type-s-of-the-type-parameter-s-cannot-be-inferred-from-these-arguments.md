---
title: Z těchto argumentů nelze odvodit datové typy parametrů typu.
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 68ed7541d76c1678f9f308ed2cda8afec1231a73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608716"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>Z těchto argumentů nelze odvodit datové typy parametrů typu.
Z těchto argumentů nelze odvodit datové typy parametrů typu. Zadání dat explicitně podaří k této chybě.  
  
 Tato chyba nastane, pokud řešení přetížení se nezdařilo. Vyskytuje se jako podřízené zprávu s oznámením, proč se odstranilo kandidát konkrétní přetížení. Chybová zpráva vysvětluje, že kompilátor nelze použít odvození typu najít datové typy parametrů typu.  
  
> [!NOTE]
>  Při zadání argumentů není možné zvolit (například pro operátory dotazu ve výrazech dotazů), zobrazí se chybová zpráva bez druhý věty.  
  
 Následující kód ukazuje chybu.  
  
```vb  
Module Module1  
  
    Sub Main()  
  
        '' Not Valid.  
        'OverloadedGenericMethod("Hello", "World")  
  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T)(ByVal x As String,   
                                      ByVal y As InterfaceExample(Of T))  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,   
                                         ByVal y As InterfaceExample(Of R))  
    End Sub  
  
End Module  
  
Interface InterfaceExample(Of T)  
End Interface  
```  
  
 **ID chyby:** BC36647 a BC36644  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Lze zadat datový typ pro parametr typu nebo parametrů, aniž byste museli spoléhat na odvození typu proměnné.  
  
## <a name="see-also"></a>Viz také:
- [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Obecné procedury v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
