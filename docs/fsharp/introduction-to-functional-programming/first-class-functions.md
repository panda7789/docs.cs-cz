---
title: Funkce první třídy
description: Další informace o funkce první třídy a jak jsou důležité pro funkční programování v F#.
ms.date: 10/29/2018
ms.openlocfilehash: 1459049c9c1c77f4eefd2a83945335b33ca22ab9
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50744620"
---
# <a name="first-class-functions"></a>Funkce první třídy

Charakteristickým znakem funkčních programovacích jazyků je povýšení funkcí do stavu první kategorie. Měli byste být schopni s funkcí provádět to, co můžete provádět s hodnotami ostatních předdefinovaných typů, a rovněž byste měli být schopni tak činit se srovnatelnou mírou úsilí.

Typická opatření stavu první kategorie zahrnují:

- Lze vázat na identifikátory funkce? To znamená můžete je přiřadit názvy?

- Můžete ukládat funkce v datové struktury, jako například v seznamu?

- Můžete předat funkci jako argument ve volání funkce?

- Může vrátit funkce z volání funkce?

Poslední dvě opatření definují to, co jsou označovány jako *operace vyššího řádu* nebo *funkce vyššího řádu*. Funkce vyššího řádu přijímají funkce jako argumenty a vrací funkce jako hodnotu volání funkce. Tyto operace podporují stěžejní části funkčního programování, jako jsou funkce mapování a skládání funkcí.

## <a name="give-the-value-a-name"></a>Přiřazení názvu hodnotě

Pokud je funkce hodnotou první kategorie, je třeba ji pojmenovat, stejně jako lze pojmenovat celá čísla, řetězce a další předdefinované typy. Na to je podle literatury o funkčním programování odkazováno jako na vázání identifikátoru na hodnotu. Jazyk F# používá [ `let` vazby](../language-reference/functions/let-bindings.md) pro vázání názvů a hodnot: `let <identifier> = <value>`. Následující kód ukazuje dva příklady.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

Funkci lze pojmenovat stejně snadno. Následující příklad definuje funkci nazvanou `squareIt` svázáním identifikátoru `squareIt` k [výraz lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`. Funkce `squareIt` má jeden parametr `n` a vrací druhou mocninu tohoto parametru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

Jazyk F# poskytuje pro dosažení stejného výsledku s kratším zápisem následující stručnější syntaxi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

Následující příklady používají pro zvýraznění podobností mezi deklaracemi funkcí a deklaracemi dalších typů hodnot převážně první styl, `let <function-name> = <lambda-expression>`. Všechny pojmenované funkce lze ale také zapsat pomocí stručnější syntaxe. Některé příklady jsou zapsány oběma způsoby.

## <a name="store-the-value-in-a-data-structure"></a>Uložení hodnoty do datové struktury

Hodnota první kategorie může být uložena v datové struktuře. Následující kód ukazuje příklady, které ukládají hodnoty v seznamech a řazených kolekcích členů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

Za účelem ověření, že název funkce uložený v řazené kolekci členů povede ve skutečnosti k vyhodnocení funkce, používá následující příklad operátory `fst` a `snd` pro získání prvního a druhého prvku z řazené kolekce členů `funAndArgTuple`. První prvek v řazené kolekci členů je `squareIt` a druhý prvek je `num`. Identifikátor `num` je v předchozím příkladu svázán s celým číslem 10, platným argumentem pro funkci `squareIt`. Druhý výraz použije první prvek v řazené kolekci členů na druhý prvek řazené kolekce členů: `squareIt num`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

Podobně jako lze identifikátor `num` zaměnit s celým číslem 10, lze zaměnit identifikátor `squareIt` s výrazem lambda `fun n -> n * n`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a>Předání hodnoty jako argumentu

Pokud hodnota patří k hodnotám stavu první kategorie jazyka, lze ji předat jako argument funkce. Je například běžné předávat jako argumenty celá čísla a řetězce. Následující kód ukazuje předání celých čísel a řetězců jako argumentů v jazyce F#.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

Pokud jsou funkce ve stavu hodnoty první kategorie, musíte být schopni je stejným způsobem předat jako argumenty. Zapamatujte si, že se jedná o první charakteristiku funkcí vyššího řádu.

V následujícím příkladu má funkce `applyIt` dva parametry, `op` a `arg`. Pokud do parametru `op` předáte funkci, která má jeden parametr, a odpovídající argument funkce předáte do parametru `arg`, funkce vrátí výsledek použití parametru `op` do parametru `arg`. V následujícím příkladu jsou oba argumenty – argument funkce a argument celého čísla – odeslány stejným způsobem, a to použitím jejich názvů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

Možnost odeslat funkci jako argument do jiné funkce je základem společných abstrakcí ve funkčních programovacích jazycích, jako jsou například operace mapování nebo filtrování. Například operace mapování je funkce vyššího řádu, která zachytává výpočet sdílený funkcemi, jež prochází seznamem, u každého prvku provedou nějakou operaci a poté vrátí seznam výsledků. Může být například třeba zvýšit každý prvek v seznamu celých čísel o jedna, každý prvek umocnit na druhou nebo převést každý prvek seznamu řetězců na velká písmena. Rekurzivní proces, který prochází seznam a vytváří seznam výsledků k vrácení, je část výpočtu náchylná k chybám. Tato část je zachycena ve funkci mapování. Jediné, co je třeba napsat pro konkrétní aplikaci, je funkce, kterou chcete použít na každý jednotlivý prvek seznamu (sčítání, umocňování, změna velikosti písmen). Tato funkce je předána jako argument funkci mapování, stejně jako je v předchozím příkladu prvek `squareIt` předán do funkce `applyIt`.

Jazyk F# poskytuje metody mapování pro většinu typů kolekcí, včetně [uvádí](../language-reference/lists.md), [pole](../language-reference/arrays.md), a [pořadí](../language-reference/sequences.md). Následující příklady používají seznamy. Syntaxe je `List.map <the function> <the list>`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

Další informace najdete v tématu [uvádí](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>Vrácení hodnoty z volání funkce

Pokud je funkce v jazyce ve stavu hodnoty první kategorie, musí být možné ji vrátit jako hodnotu volání funkce, stejně tak jako jsou vraceny další typy, jako například celá čísla a řetězce.

Následující volání funkce vrací celá čísla a zobrazí je.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

Následující volání funkce vrací řetězec.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

Následující volání funkce, deklarované na jednom řádku, vrací logickou hodnotu. Zobrazená hodnota je `True`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

Schopnost vracet funkci jako hodnotu volání funkce je druhým charakteristickým znakem funkcí vyššího řádu. V následujícím příkladu je `checkFor` definováno jako funkce, která převezme jeden argument, `item`, a jako hodnotu vrátí novou funkci. Vrácená funkce převezme seznam jako argument `lst` a v argumentu `item` vyhledá prvek `lst`. Pokud je prvek `item` nalezen, funkce vrací hodnotu `true`. Pokud není prvek `item` nalezen, funkce vrací hodnotu `false`. Stejně jako v předchozí části, následující kód používá poskytnutou funkci seznamu [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)pro prohledání seznamu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

Následující kód používá pro vytvoření nové funkce funkci `checkFor`, která přijímá jeden argument – seznam – a vyhledá v něm číslo 7.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

Následující příklad používá pro deklaraci funkce `compose`, která vrací složení dvou argumentů funkce, stav první kategorie funkcí jazyka F#.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]

>[!NOTE]
Ještě kratší verzi naleznete v následující části „Curryfikované funkce“.

Následující kód předá funkci `compose` dvě funkce jako argumenty, obě přijímající jediný argument stejného typu. Vrácená hodnota je nová funkce, která je složením obou argumentů funkce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]

>[!NOTE]
Jazyk F# obsahuje dva operátory skládající funkce, `<<` a `>>`. Například `let squareAndDouble2 = doubleIt << squareIt` je ekvivalentní zápisu `let squareAndDouble = compose doubleIt squareIt` z předchozího příkladu.

Následující příklad vrácení funkce jako hodnoty volání funkce vytvoří jednoduchou hádací hru. Pro tvorbu hry je třeba zavolat funkci `makeGame` s hodnotou, kterou má někdo uhodnout, předanou do argumentu `target`. Vrácená hodnota z funkce `makeGame` je funkce, která přijímá jeden argument (odhad) a hlásí, zda je odhad správný.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

Následující kód volá funkci `makeGame` předávající hodnotu `7` do argumentu `target`. Identifikátor `playGame` je vázán na vrácený výraz lambda. Proto funkce `playGame` přijímá jako svůj argument hodnotu funkce `guess`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a>Curryfikované funkce

Mnoho příkladů v předchozí části lze zapsat s využitím implicitního *curryfikace* v deklaracích funkcí F#. Curryfikace je proces, jenž transformuje funkci, která má více než jeden parametr do řady vložených funkcí, z nichž každá má jeden parametr. V jazyce F# jsou funkce, které mají více než jeden parametr, ze své podstaty curryfikovány. Například funkci `compose` z předchozí části lze zapsat pomocí následujícího stručného stylu se třemi parametry.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

Výsledkem je ale funkce jednoho parametru, jež vrací funkci jednoho parametru, která zase vrací jinou funkci jednoho parametru tak, jak je vidět ve funkci `compose4curried`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

K této funkci lze přistupovat několika způsoby. Každý z následujících příkladů vrátí a zobrazí číslo 18. Funkci `compose4` lze v jakémkoli příkladě nahradit funkcí `compose4curried`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

Pro ověření, zda funkce stále pracuje stejně jako dříve, lze opětovně vyzkoušet původní testovací případy.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]

>[!NOTE]
Curryfikaci lze omezit uzavřením parametrů do řazených kolekcí členů. Další informace najdete v části "Vzory parametrů" v [parametry a argumenty](../language-reference/parameters-and-arguments.md).

Následující příklad používá implicitní curryfikaci pro zápis kratší verze funkce `makeGame`. Podrobné informace o tom, jak funkce `makeGame` konstruuje a vrací funkci `game`, jsou v tomto formátu méně explicitní, ale pomocí původních testovacích případů lze ověřit, že je výsledek stejný.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

Další informace o procesu curryfikace naleznete v části "Částečné použití argumentů" v [funkce](../language-reference/functions/index.md).

## <a name="identifier-and-function-definition-are-interchangeable"></a>Definice identifikátoru a funkce jsou zaměnitelné

Název proměnné `num` je v předchozích příkladech vyhodnocen jako celé číslo 10 a není žádným překvapením, že pokud je proměnná `num` platná, číslo 10 je také platné. Totéž platí i pro identifikátory funkcí a jejich hodnoty: kdekoli lze použít název funkce, lze také použít výraz lambda, se kterým je funkce svázána.

Následující příklad definuje funkci `Boolean` s názvem `isNegative`, poté použije název funkce a následně místo něj použije její definici. Všechny tři následující příklady vracejí hodnotu `False` a zobrazují ji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

Pro provedení dalšího kroku nahraďte hodnotu, ke které je svázán identifikátor `applyIt`, hodnotou `applyIt`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>Funkce jsou hodnoty první třídy v F\#

Příklady v předchozích částech ukazují, že funkce jazyka F# splňují kritéria pro hodnoty první kategorie:

- Identifikátor lze svázat s definicí funkce.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- Funkci lze uložit v datové struktuře.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- Funkci lze předat jako argument.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- Funkci lze vrátit jako hodnotu volání funkce.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

Další informace o jazyce F#, najdete v článku [referenční dokumentace jazyka F#](../language-reference/index.md).

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující kód obsahuje všechny příklady v tomto tématu.

### <a name="code"></a>Kód

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a>Viz také:

- [Seznamy](../language-reference/lists.md)
- [Řazené kolekce členů](../language-reference/tuples.md)
- [Funkce](../language-reference/functions/index.md)
- [`let` Vazby](../language-reference/functions/let-bindings.md)
- [Výrazy lambda: `fun` – klíčové slovo](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
