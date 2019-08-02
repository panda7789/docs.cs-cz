---
title: Dokumentace XML (F#)
description: Přečtěte si informace F# o podpoře pro generování dokumentace z komentářů.
ms.date: 05/16/2016
ms.openlocfilehash: b89ab4117f4dd71126f8e203f4a5271ab3c30021
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630816"
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
|**souhrnnýtext\>/Summary \<** **\<\>**|Určuje, zda je *text* stručným popisem prvku programu. Popis je obvykle jedna nebo dvě věty.|
|_text_ **poznámky/Remarks\> \<** **\<\>**|Určuje, že *text* obsahuje doplňkové informace o prvku programu.|
|**\>** **názevparam\> = "Name" Description/param\<**  **\<**|Určuje název a popis pro funkci nebo parametr metody.|
|**\>**  **typeparam\<Name = "** název"**Popis/typeparam\<\>**|Určuje název a popis parametru typu.|
| **vrátí\</Returns\>** textu **.\<\>**|Určuje, že *text* popisuje návratovou hodnotu funkce nebo metody.|
|**\>**  **Exception\<cref = "** Type"**Description/Exception\<\>**|Určuje typ výjimky, která může být vygenerována a podmínky, za kterých je vyvolána.|
|**\>**  **Viz\<cref = "** Reference"**text/See\<\>**|Určuje vložený odkaz na jiný prvek programu. *Odkaz* je název, který se zobrazí v souboru dokumentace XML. *Text* je text zobrazený v odkazu.|
|**\>** SeeAlso cref = "Reference"/  **\<**|Určuje odkaz na další typ, který se zobrazí také v dokumentaci. *Odkaz* je název, který se zobrazí v souboru dokumentace XML. Viz také odkazy obvykle se zobrazí v dolní části stránky dokumentace.|
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
