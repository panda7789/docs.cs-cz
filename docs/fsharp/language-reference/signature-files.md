---
title: Podpis souborů (F#)
description: Další informace o použití souborů signatur F# k ukládání informací o veřejných podpisů sadu F# prvky programu, jako jsou moduly, typy a obory názvů.
ms.date: 06/15/2018
ms.openlocfilehash: f0836aa7f638dc9e2b066b0f46bbb6c086347615
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "45991230"
---
# <a name="signatures"></a>Podpisy

Soubor s podpisem obsahuje informace o veřejných podpisů sadu F# prvky programu, jako jsou moduly, typy a obory názvů. Slouží k určení usnadnění tyto prvky programu.

## <a name="remarks"></a>Poznámky

Pro každý soubor F# kód, můžete mít *soubor s podpisem*, což je soubor, který má stejný název jako soubor s kódem, ale s příponou .fsi místo .fs. Podpis souborů můžete přidat i do příkazového řádku, pokud používáte příkazový řádek přímo kompilace. K rozlišení mezi soubory s kódem a podpis soubory, soubory kódu se někdy označují jako *implementační soubory*. V projektu by měl předcházet podpisový soubor přidružen soubor kódu.

Soubor s podpisem popisuje obory názvů, moduly, typy a členy v odpovídající implementační soubor. Použijte informace v souboru signatury k určení, jaké části kódu v implementaci odpovídající soubor přístupné z kódu mimo implementační soubor a které části jsou interní v implementační soubor. Obory názvů, moduly a typy, které jsou zahrnuty v souboru signatury musí být podmnožinou obory názvů, moduly a typy, které jsou zahrnuty v souboru implementace. S několika výjimkami, které jste si poznamenali dále v tomto tématu jsou považovány za soukromé vzhledem k souboru implementace těchto prvků jazyka, které nejsou uvedené v souboru signatury. Pokud žádný podpisový soubor nenajde v projektu nebo v příkazovém řádku, použije se výchozí dostupnost.

Další informace o usnadnění výchozí, naleznete v tématu [řízení přístupu](access-control.md).

V souboru signatury ne opakujte implementace každé metody nebo funkce a definice typů. Místo toho použijte podpis pro jednotlivé metody a funkce, který se chová jako úplný specifikace funkcí, které je implementované fragment modulu nebo oboru názvů. Syntaxe pro typ podpisu je stejná jako použitý v deklaracích abstraktní metoda v rozhraní a abstraktní třídy a se také zobrazí v IntelliSense a překladač fsi.exe F# poznat správně kompilované vstup.

Pokud není k dispozici dostatek informací v signatuře typu označující, zda je zapečetěný typ, nebo zda je typ rozhraní, je nutné přidat atribut, který označuje povahu typu kompilátoru. Atributy, které používáte pro tento účel jsou popsány v následující tabulce.

|Atribut|Popis|
|---------|-----------|
|`[<Sealed>]`|Pro typ, který nemá žádné abstraktní členy nebo by neměla být rozšířena.|
|`[<Interface>]`|Pro typ, který je rozhraní.|
Kompilátor vytvoří chybu, pokud atributy nejsou konzistentní mezi podpis a deklarace v souboru implementace.

Pomocí klíčového slova `val` k vytvoření podpisu pro hodnotu nebo hodnotu funkce. Klíčové slovo `type` představuje typ podpisu.

Můžete generovat soubor podpisu pomocí `--sig` – možnost kompilátoru. Obecně platí nenapíšete .fsi soubory ručně. Místo toho pomocí kompilátoru generovat soubory .fsi, přidejte do projektu, pokud existuje a upravit tak, že odeberete metody a funkce, které nechcete, aby byl přístupný.

Existuje několik pravidel pro podpisy, typ:

- Zkratky typů v souboru implementace nesmí odpovídat typu bez zkratku v souboru signatury.

- Záznamy a rozlišovaná sjednocení musí vystavit všech nebo žádných z jejich polí a konstruktorů a pořadí v podpisu musí odpovídat pořadí v souboru implementace. Třídy lze odhalit, některé, všech nebo žádných z jejich polí a metod v podpisu.

- Třídy a struktury, které mají konstruktory musí vystavit deklarace základní třídy ( `inherits` prohlášení). Také třídy a struktury, které mají konstruktory musí vystavit všechny abstraktní metody a interface deklarace.

- Typy rozhraní musí odhalit, jejich metod a rozhraní.

Pravidla pro hodnotu podpisy jsou následující:

- Modifikátory přístupnosti (`public`, `internal`, a tak dále) a `inline` a `mutable` modifikátorů v podpisu musí odpovídat názvům v implementaci.

- Musí odpovídat počtu parametrů obecného typu (buď odvozené implicitně nebo explicitně deklarované) a typy a omezení typu u parametrů obecného typu se musí shodovat.

- Pokud `Literal` atribut se používá, musí být uvedena v signatuře a implementaci a stejnou hodnotu literálu musí používat pro obě služby.

- Vzor parametry (označované také jako *Arita*) podpisů a implementace musí být konzistentní vzhledem k aplikacím.

- Pokud názvy parametrů v souboru signatury se liší od odpovídající implementační soubor, název v souboru signatury se použije místo toho, které můžou způsobovat problémy při ladění a profilování. Pokud budete chtít informováni o tyto problémy, povolení upozornění 3218 v souboru projektu nebo při vyvolání kompilátoru (viz `--warnon` pod [– možnosti kompilátoru](compiler-options.md)).

Následující příklad kódu ukazuje příklad souboru podpisu, který má obor názvů, modulu, typu podpisy spolu s příslušnými atributy a hodnoty funkce. Také ukazuje odpovídající implementační soubor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

Následující kód ukazuje implementační soubor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Řízení přístupu](access-control.md)
- [Možnosti kompilátoru](compiler-options.md)
