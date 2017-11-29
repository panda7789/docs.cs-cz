---
title: "Refaktoring do čistého funkce (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d0a1b8d314cf1403ef5065e5432f7acd15ebb440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Refaktoring do čistého funkce (Visual Basic)
Důležitým aspektem čistý funkční transformace je naučit se Refaktorovat kódu pomocí čistý funkce.  
  
 Jak je uvedeno dříve v této části, čistou funkci má dva užitečné charakteristiky:  
  
-   Nemá žádné vedlejší účinky. Funkce nezmění žádné proměnné nebo data mimo funkci libovolného typu.  
  
-   Je konzistentní. Zadané stejnou sadu vstupních dat, vždy vrátí stejné výstupní hodnotu.  
  
 Přechod do funkčního programování jeden ze způsobů je refaktorovat stávajícího kódu pro vyloučení nepotřebných vedlejší efekty a externí závislosti. Tímto způsobem můžete vytvořit čistě funkce verzích existujícího kódu.  
  
 Toto téma popisuje je čistě funkce a co není. [Kurz: manipulace s obsahu v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurz ukazuje, jak pracovat s dokumentem WordprocessingML a obsahuje dva příklady, jak k refactor pomocí čistou funkci.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Odstranění vedlejší efekty a externí závislosti  
 Následující příklady kontrastu dvě-čistý funkce a čistou funkci.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Čistý funkce, která změní člena třídy  
 V následujícím kódu `HypenatedConcat` funkce není čistou funkci, protože upravuje `aMember` – datový člen třídy:  
  
```vb  
Module Module1  
    Dim aMember As String = "StringOne"  
  
    Public Sub HypenatedConcat(ByVal appendStr As String)  
        aMember = aMember & "-" & appendStr  
    End Sub  
  
    Sub Main()  
        HypenatedConcat("StringTwo")  
        Console.WriteLine(aMember)  
    End Sub  
End Module  
```  
  
 Tento kód vytvoří následující výstup:  
  
```  
StringOne-StringTwo  
```  
  
 Všimněte si, že je irelevantní, jestli má data upravována `public` nebo `private` získat přístup, nebo je `shared` nebo členem instance. Čistý funkce nemění žádná data mimo funkci.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Čistý funkce, která změní Argument  
 Následující verze této stejné funkce navíc není čistá, protože upravuje obsah parametru, `sb`.  
  
```vb  
Module Module1  
    Public Sub HypenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)  
        sb.Append("-" & appendStr)  
    End Sub  
  
    Sub Main()  
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")  
        HypenatedConcat(sb1, "StringTwo")  
        Console.WriteLine(sb1)  
    End Sub  
End Module  
```  
  
 Tato verze programu vytváří stejný výstup jako první verze, protože `HypenatedConcat` funkce změnila hodnota (stav) její první parametr vyvoláním <xref:System.Text.StringBuilder.Append%2A> – členská funkce. Všimněte si, že dojde k této změnou i přes tato skutečnost, `HypenatedConcat` používá předávání volání hodnotu parametru.  
  
> [!IMPORTANT]
>  U typů odkazu Pokud předáte parametr podle hodnoty, výsledkem kopii odkaz na objekt předávány. Tato kopie je stále spojena se stejná data jako odkaz na původní instanci (dokud proměnnou odkaz je přiřazen k vytvoření nového objektu). Volání odkazem není nezbytně nutné pro funkci, kterou chcete upravit parametr.  
  
### <a name="pure-function"></a>Čistý – funkce  
 Tato další verze programu hows jak implementovat `HypenatedConcat` fungovat jako čistou funkci.  
  
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
  
 Znovu, tato verze vytváří na stejný řádek výstupu: `StringOne-StringTwo`. Všimněte si, že pokud chcete zachovat zřetězených hodnota, je uložený v proměnnou zprostředkující `s2`.  
  
 Jeden z přístupů, může být velmi užitečná je zápis funkce, které jsou místně znečištěná (to znamená, že deklarace a upravit místní proměnné), ale jsou globálně čistý. Takové funkce mají mnoho společných vlastností s žádoucí composability, ale některé z více convoluted funkční programovací idioms, jako je například nutnosti použít rekurzi při totéž by provést jednoduché smyčky vyhnout.  
  
## <a name="standard-query-operators"></a>Standardní operátory dotazu  
 Důležitou vlastností objektu standardní operátory dotazu je, že jsou implementované jako čistý funkce.  
  
 Další informace najdete v tématu [standardní dotaz přehled operátory (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Úvod do čistého funkční transformace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Funkční programování vs. Imperativní programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
