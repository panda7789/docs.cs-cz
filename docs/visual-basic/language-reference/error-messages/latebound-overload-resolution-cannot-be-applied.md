---
title: Rozpoznání přetížené procedury s pozdní vazbou nelze použít pro '<procedurename>', protože přistupující instance je typu rozhraní.
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 8ceff80842ec4e7364a55578c1c3fdb870c73ece
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661974"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a>Přetížení rozpoznání s pozdní vazbou nelze použít pro '\<název_procedury >' protože přistupující instance je typu rozhraní
Kompilátor se pokouší rozpoznat odkaz na přetížená vlastnost nebo procedura, ale odkaz se nezdaří, protože argument je typu `Object` a odkazující objekt má datový typ rozhraní. `Object` Argument vynutí, aby kompilátor přeložit odkaz na jako s pozdní vazbou.  
  
 Za těchto okolností přeloží kompilátor přetížení prostřednictvím implementující třídu namísto prostřednictvím základní rozhraní. Pokud třída přejmenuje některou z přetížených verzí, kompilátor nebere v úvahu tuto verzi si přetížení, protože se její název liší. To pak způsobí, že kompilátor bude ignorovat přejmenované verze, když ho mohla se přeložit odkaz na správnou volbu.  
  
 **ID chyby:** BC30933  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použití `CType` přetypovat argument od `Object` na typ určený signatura přetížení, které chcete volat.  
  
     Mějte na paměti, že to nepomůže objekt přetypujte na odkazující na základní rozhraní. Musíte přetypovat argument lze vyvarovat této chyby.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje volání přetížený `Sub` proceduru, která způsobí, že tuto chybu v době kompilace.  
  
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
  
 V předchozím příkladu, pokud kompilátor může volání `s1` jak je uvedená, řešení by proběhnout prostřednictvím třídy `c1` namísto rozhraní `i1`. To znamená, že by kompilátor zvažte `s2` vzhledem k tomu, že je její název liší `c1`, i když je správnou volbu podle definice `i1`.  
  
 Opravte chybu tak, že změníte volání na buď následující řádky kódu:  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Jednotlivé řádky kódu, předchozí explicitní přetypování `Object` proměnnou `o1` na jeden z typů parametrů definovaných pro přetížení.  
  
## <a name="see-also"></a>Viz také:

- [Přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Řešení přetížení](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)
