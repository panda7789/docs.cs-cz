---
title: "Z těchto argumentů nelze odvodit datové typy parametrů typu."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b290c25286dce2236823919e8287db9abefc0dd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
