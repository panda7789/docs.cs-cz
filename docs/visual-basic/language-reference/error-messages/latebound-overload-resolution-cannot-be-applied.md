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
ms.openlocfilehash: 1fe3c4a29b542302b3615459142a3c565aa8244f
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513028"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a>Rozlišení přetěžování lateBound nejde použít pro proceduru instanceName >, protože přistupující instance je typ rozhraní.\<

Kompilátor se pokouší přeložit odkaz na přetíženou vlastnost nebo proceduru, ale odkaz se nezdaří, protože argument je typu `Object` a odkazující objekt má datový typ rozhraní. `Object` Argument vynutí, aby kompilátor vyřešil odkaz jako pozdní vazbu.

Za těchto okolností kompilátor vyřeší přetížení prostřednictvím implementující třídy místo přes základní rozhraní. Pokud třída přejmenuje jednu z přetížených verzí, kompilátor nepovažuje tuto verzi za přetížení, protože se její název liší. Tím dojde k tomu, že kompilátor ignoruje přejmenovanou verzi, pokud by mohla být správná volba pro vyřešení odkazu.

**ID chyby:** BC30933

## <a name="to-correct-this-error"></a>Oprava této chyby

- Použijte `CType` k přetypování argumentu `Object` z na typ určený signaturou přetížení, které chcete volat.

  Všimněte si, že neumožňuje přetypovat odkazující objekt na základní rozhraní. Chcete-li se této chybě vyhnout, je nutné přetypovat argument.

## <a name="example"></a>Příklad

Následující příklad ukazuje volání `Sub` přetížené procedury, která způsobuje tuto chybu v době kompilace.

```vb
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

V předchozím příkladu, pokud kompilátor povolil volání `s1` jako zapsáno, řešení by mělo probíhat prostřednictvím třídy `c1` namísto rozhraní `i1`. To by znamenalo, že kompilátor nebere `s2` v `c1`úvahu, že se jedná o jiný název, i když je správná volba definovaná pomocí `i1`.

Chybu můžete opravit tak, že změníte volání na některý z následujících řádků kódu:

```vb
refer.s1(CType(o1, Integer))
refer.s1(CType(o1, Double))
```

Každý z předchozích řádků kódu explicitně přetypování `Object` proměnnou `o1` na jeden z typů parametrů definovaných pro přetížení.

## <a name="see-also"></a>Viz také:

- [Přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Řešení přetížení](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)
