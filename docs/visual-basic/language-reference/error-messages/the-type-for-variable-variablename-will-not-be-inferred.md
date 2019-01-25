---
title: Typ proměnné &#39; &lt;NázevProměnné&gt; &#39; nebude odvozen, protože je vázán k poli v ohraničujícím oboru
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: 6adcc1c2a449c9192e488a5d714e1c3271568be0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672380"
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>Typ proměnné &#39; &lt;NázevProměnné&gt; &#39; nebude odvozen, protože je vázán k poli v ohraničujícím oboru
Typ pro proměnnou '\<NázevProměnné >' nebude odvozen, protože je vázán k poli v ohraničujícím oboru. Změňte název "\<NázevProměnné >", nebo použijte plně kvalifikovaný název (například 'Me.variablename' nebo "MyBase.variablename").  
  
 Řídicí proměnná smyčky for v kódu má stejný název jako pole třídy nebo jiných nadřazeném oboru. Protože proměnné ovládacího prvku se používá bez `As` klauzule, je svázaná s daným polem v nadřazeném oboru, a kompilátor pro něj vytvořit novou proměnnou nebo odvodit typ.  
  
 V následujícím příkladu `Index`, proměnné ovládacího prvku v `For` příkazu je vázán na `Index` pole `Customer` třídy. Kompilátor nevytvoří nové proměnné pro proměnnou ovládacího prvku `Index` nebo jeho typ odvodit.  
  
```  
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
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o tom, jak skrýt upozornění nebo jak zpracovávat upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42110  
  
### <a name="to-address-this-warning"></a>Chcete-li vyřešit tato upozornění  
  
-   Díky řídicí proměnná smyčky for místní změny jeho názvu identifikátor, který není také název pole třídy.  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   Vysvětlení, že řídicí proměnná smyčky for váže pole třídy jsou `Me.` k názvu proměnné.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   Aniž byste museli spoléhat na odvození místního typu, použijte `As` klauzule zadat typ řídicí proměnná smyčky for.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje předchozí příklad s první opravu na místě.  
  
```  
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
- [Postupy: Odkazování na aktuální instanci objektu](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
