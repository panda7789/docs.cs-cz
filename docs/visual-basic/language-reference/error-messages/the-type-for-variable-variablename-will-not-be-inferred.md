---
title: Typ pro proměnnou '<variablename>' nebude odvozen, protože je připojen k poli v ohraničujícím oboru.
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: e56529919945558df178e18a83a895a79bfe4919
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512726"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>Typ proměnné '\<Variable > ' nebude odvozen, protože je svázán s polem v ohraničujícím oboru

Typ proměnné '\<Variable > ' nebude odvozen, protože je svázán s polem v ohraničujícím oboru. Buď změňte název "\<Variable název >", nebo použijte plně kvalifikovaný název (například "já. Variable" nebo "MyBase. Variable").

Řídicí proměnná smyčky v kódu má stejný název jako pole třídy nebo jiný ohraničující obor. Vzhledem k tomu, že proměnná ovládacího prvku `As` se používá bez klauzule, je svázána s polem v ohraničujícím oboru a kompilátor pro něj nevytvoří novou proměnnou nebo odvodí její typ.

V následujícím příkladu `Index`je proměnná ovládacího prvku `For` v příkazu svázána `Customer` s `Index` polem ve třídě. Kompilátor nevytvoří novou proměnnou pro proměnnou `Index` ovládacího prvku nebo odvodí její typ.

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

    ' The following line will raise this warning.
        For Index = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

Ve výchozím nastavení je tato zpráva upozornění. Informace o tom, jak skrýt upozornění nebo jak zacházet s upozorněními jako s chybami, najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

**ID chyby:** BC42110

### <a name="to-address-this-warning"></a>Řešení tohoto upozornění

- Nastavte proměnnou ovládacího prvku smyčky místně změnou jejího názvu na identifikátor, který není zároveň názvem pole třídy.

  ```vb
  For I = 1 To 10
  ```

- Objasnění, že řídicí proměnná smyčky se váže k poli Class pomocí prefixování `Me.` k názvu proměnné.

  ```vb
  For Me.Index = 1 To 10
  ```

- Namísto spoléhání na odvození místního typu, použijte `As` klauzuli k určení typu pro proměnnou ovládacího prvku smyčky.

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a>Příklad
 Následující kód ukazuje předchozí příklad s první opravou na místě.

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

        For I = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

## <a name="see-also"></a>Viz také:

- [Příkaz Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Postupy: Odkaz na aktuální instanci objektu](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
