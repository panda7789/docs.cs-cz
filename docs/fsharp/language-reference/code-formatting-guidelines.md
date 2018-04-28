---
title: Pravidla formátování kódu (F#)
description: 'Další kód odsazení formátování pokyny pro programovací jazyk pro čitelnost, estetiku, standardizace a kompilace F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: a16378b42e7d2acd44dcfe0af7c68a55e4be41d1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="code-formatting-guidelines"></a>Pravidla formátování kódu

Toto téma shrnuje kód odsazení pokyny pro F #. Jazyk F # je citlivá na konce řádků a odsazení, a proto není právě čitelnost problém, estetické problém nebo problém kódování standardizace k formátování kódu správně. Je třeba naformátovat kódu správně pro něj pro správnou kompilaci.


## <a name="general-rules-for-indentation"></a>Obecná pravidla pro odsazení
Pokud je požadována odsazení, je nutné použít mezery, tabulátory není. Je vyžadován alespoň jeden prostor. Vaše organizace můžete vytvořit kódování standardy k určení počtu prostory pro odsazení; tři nebo čtyři prostory odsazení na každé úrovni, kde dochází k odsazení je typické. Můžete nakonfigurovat tak, aby odpovídaly vaší organizace odsazení standardy změnou možnosti v aplikaci Visual Studio `Options` dialogové okno, která je k dispozici z `Tools` nabídky. V `Text Editor` uzlu, rozbalte položku `F#` a pak klikněte na tlačítko `Tabs`. Popis dostupných možností najdete v tématu [možnosti, textový Editor, všechny jazyky, karty](https://msdn.microsoft.com/library/7sffa753.aspx).

Obecně platí když kompilátor analyzuje kódu, udržuje interní zásobníku, který označuje aktuální úroveň vnoření. Při představují odsazení kódu novou úroveň vnoření je vytvořen nebo nabídnutých do této interní zásobníku. Při ukončení konstrukt, úroveň je odebrány. Odsazení je jedním ze způsobů signál konec úrovní a pop interní zásobníku, ale některé tokeny také způsobit na úroveň být odebrány, jako `end` – klíčové slovo, nebo pravé složené závorce nebo závorky.

Kód na Víceřádkový konstrukce, jako je například typ definice, definice funkce `try...with` konstrukce a opakování ve smyčce konstrukce, musí být odsazeny relativně k otevírání řádku konstruktu. První řádek zobrazují odsazené určuje pozici sloupce pro následné kódu ve stejné konstrukce. Je volána úrovně odsazení *kontextu*. Pozice sloupec Nastaví minimální sloupci, označuje jako *offside řádku*, pro následující řádky kódu, které jsou ve stejné oblasti. Když je zjistil řádek kódu se zobrazují odsazené méně než této pozice zavedených sloupec, kompilátor předpokládá, že kontext skončila a že je nyní implementován na další úrovni, v rámci předchozí. Termín *offside* se používá k popisu stavu, ve kterém řádek kódu aktivuje konec konstrukt, protože není dostatečně odsazeny. Jinými slovy kód nalevo od offside řádku je offside. V kódu správně zobrazují odsazené využít výhod offside pravidlo Chcete-li zobrazit konec konstrukce. Pokud používáte odsazení nesprávně, podmínku offside může způsobit kompilátoru vydat varování nebo může vést k nesprávné interpretaci vašeho kódu.

Offside řádků je stanoven následujícím způsobem.


- `=` Token přidružený `let` zavádí řádku s offside ve sloupci prvního tokenu po `=` přihlášení.


- V `if...then...else` výrazu, sloupec pozice prvního tokenu po `then` – klíčové slovo nebo `else` – klíčové slovo zavádí offside řádku.


- V `try...with` výrazu, první token po `try` zavádí offside řádku.


- V `match` výrazu, první token po `with` a první token po každém z nich `->` zavést offside řádky.


- První token po `with` v typu rozšíření zavádí offside řádku.


- První token po provedení závorka nebo závorky, nebo až když `begin` – klíčové slovo, představuje offside řádku.


- První znak v klíčová slova `let`, `if`, a `module` zavést offside řádky.


Následující příklady kódu ilustrují pravidel odsazení. Zde tiskové příkazy spoléhají na odsazení a přiřadit je k odpovídající kontext. Pokaždé, když odsazení posune, kontext je odebrány a vrátí do předchozí kontextu. Proto je vytištěno mezeru na konci každé iteraci; "Hotovo!" je pouze vytištěno jednou, protože offside odsazení určuje, že není součástí smyčky. Tisk řetězce "Nejvyšší úrovně kontextu" není součástí funkce. Proto vytištění nejdřív během inicializace statické, než je tato funkce volána.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet1.fs)]

Výstup je následující.

```
Top-level context

(Negative number) Zero 1 2 3 Done!
```

Pokud zrušíte dlouhé řádky, musí být pokračování řádku odsazeny farther than nadřazených konstrukce. Argumenty funkce musí být například odsazeny farther than první znak názvu funkce, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet2.fs)]

Existují výjimky pro tato pravidla, jak je popsáno v následující části.


## <a name="indentation-in-modules"></a>Odsazení v modulech
Kód v místním modulu musí odsazeny relativně k modulu, ale kód v nejvyšší úrovně modulu nemusí být zobrazují odsazené. Namespace prvky nemají odsazení.

Následující příklady kódu znázornění.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet3.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet4.fs)]

Další informace najdete v tématu [moduly](modules.md).


## <a name="exceptions-to-the-basic-indentation-rules"></a>Výjimky z pravidel základní odsazení
Obecně platí, jak je popsáno v předchozí části, je, že musí být kód v Víceřádkový konstrukce odsazeny relativně k odsazení prvního řádku konstruktu a že konec konstruktu je dáno při první řádek offside. Výjimku z pravidla o při kontexty koncový je, že některé konstrukce, jako například `try...with` výrazu `if...then...else` výraz a použití `and` syntaxe deklarace vzájemně rekurzivní funkce nebo typy, mají více částí. Odsazovat novější částí, jako například `then` a `else` v `if...then...else` výraz na stejné úrovni jako token, který spustí výraz, ale místo označující element end do kontextu, představuje v další části stejného kontextu. Proto `if...then...else` výraz může být napsán jako v následujícím příkladu kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet5.fs)]

Výjimka, která má offside pravidla se vztahují pouze na `then` a `else` klíčová slova. Proto i když se nejedná o chybu pro odsazení `then` a `else` navíc nedaří odsazovat řádky kódu v `then` bloku vyvolá upozornění. To je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet6.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet7.fs)]

Pro kód ve `else` bloku další zvláštní pravidlo vztahuje. Upozornění v předchozím příkladu se zobrazí pouze na kód v `then` bloku, nikoli na kód `else` bloku. To umožňuje psát kód, který zjišťuje různé podmínky na začátku funkce bez vynucení zbytek kódu pro funkce, které je možné `else` bloku odsazení. Proto můžete napsat následující bez vytváření upozornění.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet8.fs)]

Další výjimku pro pravidlo, které při řádek není odsazeny, pokud jde o předchozí řádek je zaváděcí operátorů, například ukončit kontexty `+` a `|>`. Řádky, které začínají zaváděcí operátory jsou povolené zahájíte `(1 + oplength)` sloupce před normální pozice bez aktivace element end do kontextu, kde `oplength` je počet znaků, které tvoří operátor. To způsobí, že první token po výskytu operátoru vyrovnání v předchozím řádku.

Například v následujícím kódu `+` symbol smí být zobrazují odsazené dva sloupce a menší než předchozí řádek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet9.fs)]

Přestože odsazení obvykle zvyšuje úroveň vnoření začne být vyšší, existuje několik konstrukce kompilátor ve kterých umožňuje obnovit odsazení nižší pozici sloupce.

Konstrukce, které umožňují obnovení pozici sloupce jsou následující:


- Těla anonymní funkce. V následujícím kódu tiskové výraz začíná na pozici sloupce, který je dále vlevo než `fun` – klíčové slovo. Ale nesmí řádku spustit ve sloupci nalevo od začátku předchozí úrovně odsazení (který je nalevo od `L` v `List`).
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet10.fs)]

- Konstrukce uzavřený v závorkách nebo pomocí `begin` a `end` v `then` nebo `else` blokovat z `if...then...else` zadán výraz, odsazení je méně než pozici sloupce `if` – klíčové slovo. Tato výjimka umožňuje kódování styl, ve kterém levá závorka nebo `begin` se používá na konci řádku po `then` nebo `else`.


- Těla modulů, třídy, rozhraní a struktury oddělená `begin...end`, `{...}`, `class...end`, nebo `interface...end`. To umožňuje styl, ve kterém může být otevírání – klíčové slovo typu v definici na stejném řádku jako název typu bez vynucení celý text jako zobrazují odsazené farther than – klíčové slovo otevírání.
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet13.fs)]


## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)
