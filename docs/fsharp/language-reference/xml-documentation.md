---
title: dokumentace XML
description: Přečtěte si informace F# o podpoře pro generování dokumentace z komentářů.
ms.date: 05/16/2016
ms.openlocfilehash: 0a87915c361fc88f0c05264e1c17278fd656a167
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344693"
---
# <a name="xml-documentation"></a>dokumentace XML

Můžete získat dokumentaci z komentáře kódu třikrát lomítka (///) v F#. Komentáře XML mohou předcházet deklarace v souborech Code (. FS) nebo signaturách (. fsi).

## <a name="generating-documentation-from-comments"></a>Generování dokumentace z komentářů

Podpora F# pro generování dokumentace z komentářů je stejná jako v jiných .NET Framework jazycích. Stejně jako v jiných .NET Framework jazycích vám [možnost kompilátoru-doc](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) umožňuje vytvořit soubor XML, který obsahuje informace, které můžete převést do dokumentace pomocí nástroje, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB). Dokumentace vygenerovaná pomocí nástrojů, které jsou navrženy pro použití se sestaveními, která jsou napsána v jiných .NET Framework jazycích, obecně vytvářejí zobrazení rozhraní API, které je založeno na F# zkompilované formě konstrukcí. Pokud nástroje specificky F#nepodporují, dokumentace vygenerovaná těmito nástroji neodpovídá F# zobrazení rozhraní API.

Další informace o tom, jak vygenerovat dokumentaci z XML, najdete v tématu [ &#40;průvodce&#35; &#41;programováním dokumentačních komentářů jazyka C](https://msdn.microsoft.com/library/b2s063f7).

## <a name="recommended-tags"></a>Doporučené značky

Existují dva způsoby, jak zapsat dokumentační komentáře XML. Jedním z nich je pouze zápis dokumentace přímo v komentáři se třemi lomítky bez použití značek XML. Pokud to uděláte, celý text komentáře je pořízen jako souhrnná dokumentace pro konstrukci kódu, který následuje bezprostředně po. Tuto metodu použijte, pokud chcete zapsat pouze stručný souhrn pro každou konstrukci. Druhou metodou je použití značek XML k poskytnutí další strukturované dokumentace. Druhá metoda umožňuje zadat samostatné poznámky pro krátký souhrn, další poznámky, dokumentaci pro každý parametr a parametr typu a vyvolané výjimky a popis návratové hodnoty. V následující tabulce jsou popsány značky XML, F# které jsou rozpoznány v komentářích kódu XML.

|Syntaxe značky|Popis|
|----------|-----------|
|**\<c\>** _text_ **\</c\>**|Určuje, že *text* je kód. Tuto značku mohou použít generátory dokumentace k zobrazení textu v písmu, které je vhodné pro kód.|
|**\<summary\>** _text_ **\</Summary\>**|Určuje, zda je *text* stručným popisem prvku programu. Popis je obvykle jedna nebo dvě věty.|
|**\<poznámky\>** _text_ **\</Remarks\>**|Určuje, že *text* obsahuje doplňkové informace o prvku programu.|
|**\<param Name = "** _Name_ **"\>** _Description_ **\</param\>**|Určuje název a popis pro funkci nebo parametr metody.|
|**\<typeparam název = "** _název_ **"\>** _Popis_ **\</typeparam\>**|Určuje název a popis parametru typu.|
|**\<vrátí**  _text_\> **\</Returns\>**|Určuje, že *text* popisuje návratovou hodnotu funkce nebo metody.|
|**\<Exception cref = "** _Type_ **"\>** _Description_ **\</Exception\>**|Určuje typ výjimky, která může být vygenerována a podmínky, za kterých je vyvolána.|
|**\<viz cref = "** _reference_ **"\>** _text_ **\</See\>**|Určuje vložený odkaz na jiný prvek programu. *Odkaz* je název, který se zobrazí v souboru dokumentace XML. *Text* je text zobrazený v odkazu.|
|**\<SeeAlso cref = "** _reference_ **"/\>**|Určuje odkaz na další typ, který se zobrazí také v dokumentaci. *Odkaz* je název, který se zobrazí v souboru dokumentace XML. Viz také odkazy obvykle se zobrazí v dolní části stránky dokumentace.|
|**\<para\>** _text_ **\</para\>**|Určuje odstavec textu. Slouží k oddělení textu uvnitř značky **poznámky** .|

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následuje typický dokumentační komentář XML v souboru signatury.

### <a name="code"></a>Kód

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje alternativní metodu bez značek XML. V tomto příkladu je celý text v komentáři považován za souhrn. Všimněte si, že pokud nezadáte souhrnnou značku explicitně, neměli byste zadávat jiné značky, jako je například **param** nebo **vracet** značky.

### <a name="code"></a>Kód

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Možnosti kompilátoru](compiler-options.md)
