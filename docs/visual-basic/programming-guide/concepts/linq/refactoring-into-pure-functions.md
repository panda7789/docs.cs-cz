---
title: Refaktoring do čistých funkcí (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 0a37b30278c850256355612cec09a4c017c7adc2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379715"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Refaktoring do čistých funkcí (Visual Basic)

Důležitou součástí čistě funkčním transformacím je učit, jak Refaktorovat kód pomocí čisté funkce.

Jak je uvedeno dříve v této části, čistě funkci má dvě užitečné vlastnosti:

- Nemá žádné vedlejší účinky. Funkce nezmění žádné proměnné nebo dat libovolného typu mimo funkci.

- To je konzistentní. S ohledem stejnou sadu vstupních dat, vždycky vrátí stejnou hodnotu výstup.

 Jeden způsob, jak přechod do funkčního programování je Refaktorujte již existující kód k odstranění nepotřebných vedlejší účinky a externích závislostí. Tímto způsobem můžete vytvořit čistě funkce verze stávajícího kódu.

Toto téma popisuje čistě funkce je a co není. [Kurzu: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurz ukazuje, jak pracovat s dokumentu WordprocessingML a obsahuje dva příklady toho, jak refaktorace pomocí čisté funkce.

## <a name="eliminating-side-effects-and-external-dependencies"></a>Odstranění vedlejší účinky a externí závislosti

Následující příklady kontrastu dvě funkce čistě a čistě funkce.

### <a name="non-pure-function-that-changes-a-class-member"></a>Čistě funkce, která se mění členem třídy.

V následujícím kódu `HyphenatedConcat` funkce není čistě funkcí, protože upravuje `aMember` datový člen třídy:

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

Tento kód vytvoří následující výstup:

```
StringOne-StringTwo
```

Všimněte si, že je bezvýznamná toho, jestli má úpravy dat `public` nebo `private` přístup, nebo je `shared` člen nebo člen instance. Čistě funkce nemění žádná data mimo funkci.

### <a name="non-pure-function-that-changes-an-argument"></a>Čistě funkce, která se mění Argument

Následující verze stejné funkce kromě toho není čistě, protože mění obsah svůj parametr, `sb`.

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

Tuto verzi programu vytváří stejný výstup jako první verze, protože `HyphenatedConcat` funkce změnila jejím prvním parametrem (stav) hodnota vyvoláním <xref:System.Text.StringBuilder.Append%2A> členskou funkci. Všimněte si, že tato změna nastane bez ohledu na tom, který `HyphenatedConcat` používá předávání parametrů volání podle hodnoty.

> [!IMPORTANT]
> Pro typy odkazů Pokud předáte parametr podle hodnoty, výsledkem zkopírovat odkaz na objekt je předán. Tato kopie je stále spojena se stejná data jako odkaz na původní instanci (až do nového objektu přiřadí proměnná odkaz). Volání odkazem se nutně nevyžaduje pro funkci, kterou chcete upravit parametr.

### <a name="pure-function"></a>Pure – funkce

Tato další verze programu postupy implementace `HyphenatedConcat` fungovat jako čistě funkce.

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

Znovu, vytvoří tato verze stejného řádku výstupu: `StringOne-StringTwo`. Všimněte si, že pokud chcete zachovat zřetězené hodnotě, uloží se zprostředkující proměnné `s2`.

Je jedním z přístupů, které mohou být velmi užitečná k zápisu funkcí, které jsou místně znečištěná (to znamená, že deklarace a upravit místní proměnné), ale jsou globálně čistě. Tyto funkce mají mnoho vlastností žádoucí skládání, ale Vyhněte se některé z více složitými funkční programovací idiomy, jako je například museli použít rekurzi při jednoduché smyčky by provést totéž.

## <a name="standard-query-operators"></a>Standardní operátory dotazu

Důležitou vlastnost operátory standardního dotazu je, že jsou implementovány jako čistě funkce.

Další informace najdete v tématu [přehled operátory standardního dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

## <a name="see-also"></a>Viz také:

- [Úvod k čistě funkčním transformacím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Funkční programování vs. Imperativní programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
