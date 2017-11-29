---
title: "Rozpoznání přetížené nelze použít pro & č. 39; &lt;procedurename&gt;& č. 39; protože přistupující instance je typ rozhraní"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb7f8a9f6eadfc9fd856ea57d362b43d25ff81a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a>Rozpoznání přetížené nelze použít pro & č. 39; &lt;procedurename&gt;& č. 39; protože přistupující instance je typ rozhraní
Kompilátor se pokouší vyřešit odkaz na vlastnost přetížené nebo postup, ale odkaz nezdaří, protože argument je typu `Object` a odkazující objekt má datový typ rozhraní. `Object` Způsobí, že kompilátoru vyřešit jako pozdní vazbou odkaz.  
  
 Za těchto okolností přeloží kompilátor přetížení prostřednictvím implementující třídu místo prostřednictvím základní rozhraní. Pokud třída přejmenuje jednu z verzí přetížené, kompilátor nebere v úvahu této verze být přetížení, protože se její název liší. To způsobí, že kompilátoru ignorovat přejmenovat verze při by mohlo být nejvhodnější odkaz na řešení.  
  
 **ID chyby:** BC30933  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použití `CType` přetypovat argument z `Object` na typ určený podpis přetížení, které chcete volat.  
  
     Všimněte si, že nepomůže přetypovat odkazující objekt, který má základní rozhraní. Argumentem této chybě zabráníte tak musíte vysílat.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje volání přetížené `Sub` procedury, která způsobí, že tato chyba při kompilaci.  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 V předchozím příkladu, pokud je povoleno volání do kompilátoru `s1` jako zapsána, řešení by proběhnout prostřednictvím třídy `c1` místo rozhraní `i1`. To znamená, když nebude zvážit kompilátor `s2` protože se její název liší v `c1`, i když je nejvhodnější podle definice `i1`.  
  
 Chybu můžete vyřešit změnou volání na jednu z následujících řádků kódu:  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Každý předchozí řádek kódu explicitně vrhá `Object` proměnná `o1` na jeden z typů parametrů definovaný pro přetížení.  
  
## <a name="see-also"></a>Viz také  
 [Přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Řešení přetížení](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [CType – funkce](../../../visual-basic/language-reference/functions/ctype-function.md)
