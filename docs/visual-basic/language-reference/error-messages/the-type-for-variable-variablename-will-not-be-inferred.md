---
title: Typ pro proměnnou &#39; &lt;NázevProměnné&gt; &#39; nebude odvodit, protože je vázána na pole ve vymezeném oboru
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: cb423e8dcced6956eb86d484607915030c91412b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594280"
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>Typ pro proměnnou &#39; &lt;NázevProměnné&gt; &#39; nebude odvodit, protože je vázána na pole ve vymezeném oboru
Typ pro proměnnou '\<NázevProměnné >, nebude ho odvodit, protože je vázána na pole v vymezeném oboru. Změňte název '\<NázevProměnné >', nebo použijte plně kvalifikovaný název (například 'Me.variablename' nebo 'MyBase.variablename').  
  
 Řídicí proměnná smyčky v kódu má stejný název jako pole třídy nebo jiných vymezeném oboru. Protože řídicí proměnná se používá bez `As` klauzuli je vázána na pole ve vymezeném oboru a kompilátor pro něj vytvořit novou proměnnou nebo odvození jeho typu.  
  
 V následujícím příkladu `Index`, proměnné ovládacího prvku v `For` příkaz, je vázán k `Index` pole `Customer` – třída. Kompilátor nevytvoří nové proměnné pro řídicí proměnná `Index` nebo odvození jeho typu.  
  
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
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o tom, jak skrýt upozornění nebo způsobu zpracování upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42110  
  
### <a name="to-address-this-warning"></a>Pro vyřešení tohoto upozornění  
  
-   Zkontrolujte řídicí proměnná smyčky místní změnou názvu na identifikátor, který není také název pole třídy.  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   Vysvětlení, že řídicí proměnná smyčky vytvoří vazbu k poli Třída pomocí prefixu `Me.` k názvu proměnné.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   Aniž byste museli spoléhat na odvození místního typu, použijte `As` klauzule zadejte typ pro proměnnou řízení smyčky.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje předchozí příklad s první oprava na místě.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Příkaz Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Postupy: Odkazování na aktuální instanci objektu](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Me, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
