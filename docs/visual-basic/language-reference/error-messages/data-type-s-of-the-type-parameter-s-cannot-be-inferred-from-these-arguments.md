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
ms.openlocfilehash: 81535e3272eaed587288c26c4a4b9649467abed8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963565"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>Z těchto argumentů nelze odvodit datové typy parametrů typu.
Z těchto argumentů nelze odvodit datové typy parametrů typu. Je možné, že se chybu podaří odstranit explicitním zadáním datových typů.  
  
 K této chybě dojde v případě, že se nepovedlo vyřešit přetížení. K tomu dochází jako podřízená zpráva, která uvádí, proč byl vyloučen konkrétní kandidát na přetížení. Chybová zpráva vysvětluje, že kompilátor nemůže použít odvození typu k nalezení datových typů pro parametry typu.  
  
> [!NOTE]
> Pokud se zadáním argumentů nejedná o možnost (například pro operátory dotazu ve výrazech dotazu), zobrazí se chybová zpráva bez druhé věty.  
  
 Následující kód demonstruje chybu.  
  
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
  
- Možná budete moct zadat datový typ pro parametr typu nebo parametry a nemusíte se spoléhat na odvození typu.  
  
## <a name="see-also"></a>Viz také:

- [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Obecné procedury v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Převody typu v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
