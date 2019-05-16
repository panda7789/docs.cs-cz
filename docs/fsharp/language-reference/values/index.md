---
title: Hodnoty
description: Zjistěte, jak hodnoty v F# jsou množství, které mají konkrétní typ.
ms.date: 05/16/2016
ms.openlocfilehash: fe87bb568591b862737456ff92ba202ba7795e3d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641620"
---
# <a name="values"></a>Hodnoty

Hodnoty v F# jsou množství, které mají konkrétní typ; hodnoty může být integrálního typu nebo plovoucí desetinnou čárkou, znaky nebo hodnoty text, seznamy, pořadí, pole, řazených kolekcí členů, rozlišovaná sjednocení, záznamy, typy tříd nebo funkce.

## <a name="binding-a-value"></a>Po navázání hodnoty

Termín *vazby* znamená, že název přidružení definici. `let` – Klíčové slovo sváže hodnotu, stejně jako v následujících příkladech:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Typ hodnoty je odvozen z definice. Pro primitivní typ, jako je číslo s plovoucí desetinnou čárkou nebo celočíselné bod je určen typ z typu literál. Proto v předchozím příkladu, kompilátor odvodí typ `b` bude `unsigned int`, že kompilátor odvodí typ `a` bude `int`. Typ hodnoty funkci je určen z návratové hodnoty v těle funkce. Další informace o typech hodnot funkce, najdete v části [funkce](../functions/index.md). Další informace o typy literálu, naleznete v tématu [literály](../literals.md).

Kompilátor nevyvolá diagnostiky o nevyužitých vazby ve výchozím nastavení. Pro příjem těchto zpráv, povolte upozornění 1182 v souboru projektu nebo při vyvolání kompilátoru (viz `--warnon` v části [– možnosti kompilátoru](../compiler-options.md)).

## <a name="why-immutable"></a>Důvod, proč neměnné?

Neměnné hodnoty jsou hodnoty, které nelze změnit během provádění programu. Pokud se používají pro jazyky, jako je například C++, Visual Basic nebo C#, možná pro vás bude překvapení, který F# vloží nadřazenost přes neměnné hodnoty a nikoli proměnné, které je možné přiřadit nové hodnoty během provádění programu. Neměnnými daty je důležitý prvek, funkční programování. V prostředí s více vlákny jsou těžko spravuje sdílené proměnlivé proměnné, které lze změnit tím, že mnoho různých vlákna. Kromě toho s proměnlivými proměnnými, může být někdy obtížné zjistit, pokud proměnné může být změněn, pokud je předána do jiné funkce.

V čistě funkčních jazyků nejsou žádné proměnné a funkce se chovají výhradně jako matematických funkcí. Pokud kód v procedurální jazyk používá přiřazení proměnné změnit hodnotu, má ekvivalentní kód v jazyce funkční neměnné hodnotu, která je vstup, neměnné funkce a různé hodnoty neměnné jako výstup. Tato matematické přísnosti umožňuje užší důvody týkající se chování programu. Tato užší reasoning je díky kompilátory přísněji kontrolovat kód a optimalizovat efektivněji a pomáhá zjednodušit vývojářům pochopit a psát správný kód. Funkční kód je proto pravděpodobně budou snadněji ladit než běžné kódu procedury.

F#čistě funkční jazyk ještě není plně podporuje funkční programování. Použití neměnné hodnot je vhodné, protože díky tomu se váš kód, abyste využili výhod důležitou součástí funkčního programování.

## <a name="mutable-variables"></a>Proměnlivé proměnné

Můžete použít klíčové slovo `mutable` k určení proměnné, které se můžou změnit. Proměnlivé proměnné v F# by měly obecně mít omezený rozsah, jako typ pole nebo jako místní hodnota. Proměnlivé proměnné s omezeným oborem usnadňuje řízení a jsou méně pravděpodobné, že má být upraven nesprávné způsoby.

Počáteční hodnota proměnlivé proměnné můžete přiřadit pomocí `let` – klíčové slovo v stejným způsobem, jak můžete definovat hodnotu. Rozdíl je ale, že je lze následně přiřadit nové hodnoty proměnlivé proměnné pomocí `<-` operátor jako v následujícím příkladu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet602.fs)]

Hodnoty, které jsou označeny `mutable` může automaticky povýšen na `'a ref` Pokud zachycená výrazem uzávěru, včetně formuláře, které vytvářejí uzávěry, jako například `seq` tvůrci. Pokud chcete být upozorněni na k tomu dojde, varování při povolení 3180 v souboru projektu nebo při vyvolání kompilátoru.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----|-----------|
|[Vazby let](../functions/let-bindings.md)|Obsahuje informace o použití `let` – klíčové slovo pro vázání názvů a hodnot a funkcí.|
|[Funkce](../functions/index.md)|Poskytuje přehled funkcí v F#.|

## <a name="see-also"></a>Viz také:

- [Hodnoty Null](null-Values.md)
- [Referenční dokumentace jazyka F#](../index.md)
