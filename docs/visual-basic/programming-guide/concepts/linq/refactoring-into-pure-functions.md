---
title: Refaktoring do čistých funkcí
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 415b088661eca347330f4776901d68ee514d8dad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413476"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Refaktoring na čistě funkce (Visual Basic)

Důležitým aspektem čistě funkční transformace je učení, jak refaktorovat kód pomocí čistě funkcí.

Jak bylo uvedeno dříve v této části, funkce Pure má dvě užitečné charakteristiky:

- Nemá žádné vedlejší účinky. Funkce nemění žádné proměnné ani data žádného typu mimo funkci.

- Je konzistentní. V případě stejné sady vstupních dat bude vždy vracet stejnou výstupní hodnotu.

 Jedním ze způsobů, jak přecházet do funkčního programování, je refaktorující existující kód, který eliminuje nepotřebné vedlejší účinky a externí závislosti. Tímto způsobem můžete vytvářet čistě verze funkcí stávajícího kódu.

Toto téma popisuje, co je funkce Pure a co není. [Kurz: manipulace s obsahem v kurzu WordprocessingML dokumentu (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md) ukazuje, jak manipulovat s dokumentem WordprocessingML a obsahuje dva příklady refaktorování pomocí funkce Pure.

## <a name="eliminating-side-effects-and-external-dependencies"></a>Vyloučení vedlejších efektů a externích závislostí

Následující příklady kontrastují dvě nečisté funkce a funkci Pure.

### <a name="non-pure-function-that-changes-a-class-member"></a>Nečistá funkce, která mění člena třídy

V následujícím kódu není `HyphenatedConcat` funkce čistě funkcí, protože upravuje `aMember` datový člen ve třídě:

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

Výsledkem tohoto kódu je následující výstup:

```console
StringOne-StringTwo
```

Všimněte si, že je nedůležité, jestli data, která jsou měněna `public` `private` , mají přístup nebo jsou členem `shared` nebo členem instance. Funkce Pure nemění žádná data mimo funkci.

### <a name="non-pure-function-that-changes-an-argument"></a>Nečistá funkce, která mění argument

Kromě toho následující verze této funkce není čistá, protože upravuje obsah svého parametru, `sb` .

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

Tato verze programu vytvoří stejný výstup jako první verze, protože `HyphenatedConcat` funkce změnila hodnotu (stav) jeho prvního parametru vyvoláním <xref:System.Text.StringBuilder.Append%2A> členské funkce. Všimněte si, že tato změna probíhá navzdory tomu, že `HyphenatedConcat` používá předávání parametru volání podle hodnoty.

> [!IMPORTANT]
> Pro typy odkazů, Pokud předáte parametr podle hodnoty, výsledkem bude kopie odkazu na předaný objekt. Tato kopie je stále přidružená ke stejným datům instance jako původní odkaz (dokud referenční proměnná není přiřazena k novému objektu). Volání po odkazech nemusí nutně vyžadovat, aby funkce mohla upravovat parametr.

### <a name="pure-function"></a>Funkce Pure

Tato další verze programu Hows způsob implementace `HyphenatedConcat` funkce jako čistě funkce.

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

Tato verze znovu vytvoří stejný řádek výstupu: `StringOne-StringTwo` . Všimněte si, že pokud chcete zachovat zřetězenou hodnotu, je uložena v mezilehlé proměnné `s2` .

Jedním z přístupů, které mohou být velmi užitečné, je psaní funkcí, které jsou místně nečisté (to znamená, že deklarují a mění místní proměnné), ale jsou globálně čistě. Tyto funkce mají mnoho z hlediska žádoucích vlastností, ale nemusíte používat rekurzi idiomy, jako je třeba použití rekurze, když by jednoduchá smyčka mohla dosáhnout stejné věci.

## <a name="standard-query-operators"></a>Standardní operátory dotazu

Důležitou vlastností standardních operátorů dotazu je to, že jsou implementované jako čisté funkce.

Další informace najdete v tématu [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md).

## <a name="see-also"></a>Viz také

- [Úvod do čistě funkční transformace (Visual Basic)](introduction-to-pure-functional-transformations.md)
- [Funkční programování vs. imperativní programování (Visual Basic)](functional-programming-vs-imperative-programming.md)
