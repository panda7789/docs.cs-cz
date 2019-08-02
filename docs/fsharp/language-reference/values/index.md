---
title: Hodnoty
description: Přečtěte si, F# jak hodnoty v jsou množství, které má konkrétní typ.
ms.date: 05/16/2016
ms.openlocfilehash: ed7a5b069a5a47aacf0cce4cfa754ded46f6e84a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630795"
---
# <a name="values"></a>Hodnoty

Hodnoty v F# jsou množství, které má konkrétní typ; hodnoty mohou být integrální nebo plovoucí desetinné čárky, znaky nebo text, seznamy, sekvence, pole, řazené kolekce členů, rozlišené sjednocení, záznamy, typy tříd nebo hodnoty funkcí.

## <a name="binding-a-value"></a>Vytvoření vazby hodnoty

Pojem *vazba* znamená přidružení názvu k definici. `let` Klíčové slovo váže hodnotu, jak je uvedeno v následujících příkladech:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Typ hodnoty je odvozen z definice. Pro primitivní typ, jako je číslo integrálního nebo plovoucího bodu, je typ určen z typu literálu. Proto kompilátor odvodí v předchozím příkladu `b` typ, který má být `unsigned int`, zatímco kompilátor `a` odvodí typ, který má být `int`. Typ hodnoty funkce je určen z návratové hodnoty v těle funkce. Další informace o typech hodnot funkcí naleznete v tématu [Functions](../functions/index.md). Další informace o typech literálů naleznete v [](../literals.md)tématu Literal.

Kompilátor ve výchozím nastavení nevydá diagnostiku o nepoužitých vazbách. Chcete-li přijímat tyto zprávy, povolte upozornění 1182 v souboru projektu nebo při vyvolání kompilátoru (viz část `--warnon` [Možnosti kompilátoru](../compiler-options.md)).

## <a name="why-immutable"></a>Proč neměnné?

Neměnné hodnoty jsou hodnoty, které nelze změnit v průběhu provádění programu. Pokud používáte k jazykům C++, jako je Visual Basic, nebo C#, může to být překvapivé, které F# místo proměnných, které mohou být přiřazeny k novým hodnotám během provádění programu, přemístit Primacy na neměnné hodnoty. Neměnné data jsou důležitým prvkem funkčního programování. V prostředí s více vlákny jsou sdílené proměnlivé proměnné, které lze změnit pomocí mnoha různých vláken, obtížné spravovat. I s proměnlivými proměnnými může někdy být obtížné určit, zda může být proměnná změněna při předání jiné funkci.

V čistě funkčních jazycích nejsou k dispozici žádné proměnné a funkce se chovají výhradně jako matematické funkce. Kde kód v procedurálním jazyce používá přiřazení proměnné pro změnu hodnoty, ekvivalentní kód v funkčním jazyku má neproměnlivou hodnotu, která je vstupem, neproměnlivá funkce a různé neměnné hodnoty jako výstup. Tato Matematická striktní umožňuje důkladnější rozhodnutí o chování programu. Tímto užším důvodem je to, že kompilátorům umožňuje, aby se kód kontrolovalější a optimalizoval efektivněji a usnadnil vývojářům pochopení a psaní správného kódu. Funkční kód je proto pravděpodobně snazší ladit než běžný procedurální kód.

F#není čistě funkční jazyk, ale plně podporuje funkční programování. Použití neměnných hodnot je dobrý postup, protože to umožňuje vašemu kódu těžit z důležitého aspektu funkčního programování.

## <a name="mutable-variables"></a>Proměnlivé proměnné

Klíčové slovo `mutable` lze použít k určení proměnné, kterou lze změnit. Proměnlivé proměnné F# v by měly být obecně omezené oboru, buď jako pole typu, nebo jako místní hodnota. Proměnlivé proměnné s omezeným rozsahem mají snadnější kontrolu a jsou méně pravděpodobně upravovány nesprávnými způsoby.

Můžete přiřadit počáteční hodnotu proměnlivé proměnné pomocí `let` klíčového slova stejným způsobem, jako byste definovali hodnotu. Rozdíl je však, že můžete následně přiřadit nové hodnoty proměnlivým proměnným pomocí `<-` operátoru, jak je uvedeno v následujícím příkladu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet602.fs)]

Hodnoty s `mutable` označením mohou být automaticky `'a ref` povýšeny na hodnotu, pokud je zachycena uzávěrkou, včetně formulářů, `seq` které vytvářejí uzávěry, jako jsou například tvůrci. Pokud chcete být upozorněni v případě, že k tomu dojde, povolte upozornění 3180 v souboru projektu nebo při vyvolání kompilátoru.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----|-----------|
|[Vazby let](../functions/let-bindings.md)|Poskytuje informace o použití `let` klíčového slova k vytvoření vazby názvů k hodnotám a funkcím.|
|[Funkce](../functions/index.md)|Poskytuje přehled funkcí v F#nástroji.|

## <a name="see-also"></a>Viz také:

- [Hodnoty Null](null-Values.md)
- [Referenční dokumentace jazyka F#](../index.md)
