---
title: Dokumentace XML (F#)
description: Další informace o podpoře v F# pro generování dokumentace z komentářů.
ms.date: 05/16/2016
ms.openlocfilehash: a1fb5eb682ff1188136b31b64e2d7c537d2c9a0e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153641"
---
# <a name="xml-documentation"></a>dokumentace XML

Dokumentace ke službě z třemi lomítky (/ / / / /) můžete vytvářet v komentářích ke kódu F#. Komentáře XML můžete před deklaracemi v kódu souborů (.fs) nebo podpisem (.fsi).

## <a name="generating-documentation-from-comments"></a>Generování dokumentace z komentářů

Podpora v F# pro generování dokumentace z komentářů je stejný jako v jiných jazycích rozhraní .NET Framework. Stejně jako v jiných jazycích rozhraní .NET Framework [-doc – možnost kompilátoru](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) umožňuje vytvořit soubor XML, který obsahuje informace, které lze převést na dokumentaci, pomocí nástroje, jako je například Sandcastle. Dokumentace ke službě vygenerovat pomocí nástrojů, které jsou navrženy pro použití se sestaveními, která jsou napsané v jiných jazycích rozhraní .NET Framework, obecně vytvořit zobrazení rozhraní API, která je založena na kompilovaný formy F# vytvoří. Pokud nástroje specificky podporují F#, dokumentace generovaná tyto nástroje se neshoduje s F# zobrazení rozhraní API.

Další informace o tom, jak generovat dokumentaci ze souboru XML, naleznete v tématu [dokumentační komentáře XML &#40;C&#35; Průvodce programováním pro službu&#41;](https://msdn.microsoft.com/library/b2s063f7).

## <a name="recommended-tags"></a>Doporučené značky

Existují dva způsoby, jak psát komentáře dokumentace XML. Jeden je zapsat dokumentaci přímo třemi lomítky komentář, bez použití značky XML. Pokud to uděláte, celý komentář je považován za souhrnné dokumentaci pro konstrukci kódu, který následuje. Tuto metodu použijte, pokud chcete zapsat jenom stručný popis pro každou konstrukci. Jiné metody je použití značky XML jako více strukturovaných dokumentace. Druhá metoda vám umožňuje určit samostatné poznámky stručně shrnuje, další poznámky, dokumentaci pro každý parametr a typ parametrů a výjimky vyvolané a popis návratovou hodnotu. Následující tabulka popisuje značky XML, které jsou rozpoznány ve F# komentářů ke kódu XML.

|Syntaxe značek|Popis|
|----------|-----------|
|**\<c\>**_text_**\</c\>**|Určuje, že *text* je kód. Toto klíčové slovo lze generátorů dokumentace k zobrazení textu v písma, která je vhodná pro kód.|
|**\<Souhrn\>**_text_ **\< /summary\>**|Určuje, že *text* je stručný popis ovládací prvek programu. Popis je obvykle jednu nebo dvě věty.|
|**\<Poznámky\>**_text_ **\< /poznámky\>**|Určuje, že *text* obsahuje doplňující informace o prvku programu.|
|**\<Param name = "**_název_**"\>**_popis_**\</param\>**|Určuje název a popis parametru funkce nebo metody.|
|**\<typeparam name = "**_název_**"\>**_popis_**\</typeparam\>**|Určuje název a popis pro parametr typu.|
|**\<Vrátí\>**_text_ **\< /returns\>**|Určuje, že *text* popisuje návratovou hodnotu funkce nebo metody.|
|**\<Výjimka cref = "**_typ_**"\>**_popis_**\</exception\>**|Určuje typ výjimky, která je možné generovat a podmínek, za kterých je vyvolána výjimka.|
|**\<Zobrazit cref = "**_odkaz_**"\>**_text_ **\< /naleznete v tématu\>**|Určuje vložený odkaz na jiný prvek programu. *Odkaz* je název, který se zobrazí v souboru dokumentace XML. *Text* je text zobrazený v odkazu.|
|**\<SeeAlso cref = "**_odkaz_**" /\>**|Uvádí v části Viz také odkaz na dokumentaci k jinému typu. *Odkaz* je název, který se zobrazí v souboru dokumentace XML. Další informace najdete v článku odkazy obvykle zobrazují v dolní části stránky dokumentace.|
|**\<para\>**_text_**\</para\>**|Určuje odstavci textu. To se používá k oddělení text mezi **poznámky** značky.|

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následuje Typická Dokumentační komentář XML v souboru signatury.

### <a name="code"></a>Kód

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje alternativní metody bez značky XML. V tomto příkladu je celý text v komentáři považován za souhrn. Všimněte si, že pokud explicitně neurčíte souhrn značky, by neměla zadat jiné značky jako **param** nebo **vrátí** značky.

### <a name="code"></a>Kód

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Možnosti kompilátoru](compiler-options.md)
