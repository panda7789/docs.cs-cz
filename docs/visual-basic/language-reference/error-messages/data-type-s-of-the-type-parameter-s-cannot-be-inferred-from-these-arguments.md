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
ms.openlocfilehash: 6f84df5c9388220e5ca817d95362753df0920534
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586809"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>Z těchto argumentů nelze odvodit datové typy parametrů typu.
Z těchto argumentů nelze odvodit datové typy parametrů typu. Zadání dat typy explicitně může tuto chybu opravit.  
  
 K této chybě dojde, když rozlišení přetížení se nezdařilo. K tomu dochází jako podřízené zpráva oznamující, proč se odstranilo kandidátem konkrétní přetížení. Chybová zpráva vysvětluje, že kompilátor nelze použít odvození typu najít datové typy parametrů typu.  
  
> [!NOTE]
>  Při zadání argumentů není možné (například pro operátory dotazu ve výrazech dotazů), zobrazí se chybová zpráva bez druhé věty.  
  
 Následující kód ukazuje chyba.  
  
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
  
-   Je možné zadat datový typ pro parametr typu nebo parametry, aniž byste museli spoléhat na odvození typu.  
  
## <a name="see-also"></a>Viz také  
 [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Obecné procedury v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
