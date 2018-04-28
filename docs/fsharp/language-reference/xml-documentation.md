---
title: Dokumentace XML (F#)
description: 'Další informace o podpoře v jazyce F # pro generování dokumentace z komentářů.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: c9514532904f81030752bf7a4044f70a18222cab
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="xml-documentation"></a>dokumentace XML

Dokumentace z triple lomítko (/ / /) může vytvářet code komentáře v jazyce F #. Komentáře XML můžete před deklarace v kódu souborů (.fs) nebo podpis (.fsi).


## <a name="generating-documentation-from-comments"></a>Generování dokumentace z komentářů
Podpora v jazyce F # pro generování dokumentace z komentářů je stejný jako v jiných jazycích rozhraní .NET Framework. Stejně jako ostatní jazyky rozhraní .NET Framework [-doc – možnost kompilátoru](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) umožňuje vytvořit soubor XML, který obsahuje informace, které můžete převést pomocí nástroje, jako je například aplikaci Sandcastle dokumentaci. V dokumentaci vytvořen pomocí nástroje, které jsou navrženy pro použití s sestavení, které jsou zapsány v jinými jazyky rozhraní .NET Framework obecně vytvořit zobrazení rozhraní API, která je založená na kompilované formu konstrukce jazyka F #. Pokud nástroje konkrétně nepodporují F #, neodpovídá dokumentaci generované tyto nástroje F # zobrazení rozhraní API.

Další informace o tom, jak generovat dokumentaci z XML najdete v tématu [dokumentační komentáře XML &#40;C&#35; Průvodce programováním&#41;](https://msdn.microsoft.com/library/b2s063f7).


## <a name="recommended-tags"></a>Doporučené značky
Existují dva způsoby, jak zapsat dokumentační komentáře XML. Jeden je právě v dokumentaci psát přímo do komentář triple lomítko, bez použití značky XML. Pokud to uděláte, text celý komentář je považován za souhrn dokumentace pro konstrukci kódu, který následuje. Tuto metodu použijte, pokud chcete zapisovat pouze stručné souhrnné informace pro každý konstrukce. Další metodou je použití značky XML zajistit více strukturovaných dokumentace. Druhá metoda umožňuje určit samostatné poznámky pro krátký souhrn, další poznámky, dokumentace pro každý parametr a parametr typu a výjimek vyvolaných a popis návratovou hodnotu. Následující tabulka popisuje značky XML, které jsou rozpoznány v komentáře kódu XML F #.



|Syntaxe značek|Popis|
|----------|-----------|
|**&lt;c&gt;***text***&lt;/c&gt;**|Určuje, že *text* je kód. Tato značka lze dokumentaci generátory zobrazení textu v písma, který je vhodný pro kód.|
|**&lt;Souhrn&gt;***text*** &lt; /souhrn&gt;**|Určuje, že *text* je stručný popis programu elementu. Popis je obvykle jednu nebo dvě věty.|
|**&lt;Poznámky&gt;***text*** &lt; /remarks&gt;**|Určuje, že *text* obsahuje doplňující informace o elementu, program.|
|**&lt;Název parametru = "***název***"&gt;***popis***&lt;/param&gt;**|Určuje název a popis pro parametr funkce nebo metoda.|
|**&lt;typeparam name = "***název***"&gt;***popis***&lt;/typeparam&gt;**|Určuje název a popis pro parametr typu.|
|**&lt;Vrátí&gt;***text*** &lt; /vrátí&gt;**|Určuje, že *text* popisuje vrácenou hodnotu funkci nebo metodu.|
|**&lt;Výjimka cref = "***typ***"&gt;***popis***&lt;/exception&gt;**|Určuje typ výjimky, která se dá vygenerovat a v případech, za kterých je vyvolána.|
|**&lt;v tématu cref = "***odkaz***"&gt;***text*** &lt; /najdete na&gt;**|Určuje vložený odkaz na jiný program element. *Odkaz* je název, který se zobrazuje v souborů dokumentace XML. *Text* je text uvedený odkaz.|
|**&lt;Viz také cref = "***odkaz***" /&gt;**|Určuje odkaz v části Viz také v dokumentaci k jinému typu. *Odkaz* je název, který se zobrazuje v souborů dokumentace XML. Další informace najdete v článku odkazy obvykle zobrazují v dolní části stránky dokumentace.|
|**&lt;para&gt;***text***&lt;/para&gt;**|Určuje odstavec textu. To slouží k oddělení text v rámci **poznámky** značky.|

## <a name="example"></a>Příklad

### <a name="description"></a>Popis
Následuje typický komentáře dokumentace XML v souboru.


### <a name="code"></a>Kód
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]
    
## <a name="example"></a>Příklad

### <a name="description"></a>Popis
Následující příklad ukazuje alternativní metodu, bez použití značek XML. V tomto příkladu se celý text v komentář považuje souhrn. Všimněte si, že pokud explicitně nezadáte přehled značek, by neměl zadáte jiné značky, jako **param** nebo **vrátí** značky.


### <a name="code"></a>Kód
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]
    
## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Možnosti kompilátoru](compiler-options.md)
