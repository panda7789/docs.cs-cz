---
title: Soubory signatur
description: Naučte se používat F# soubory signatur k ukládání informací o veřejných podpisech sady prvků F# programu, jako jsou typy, obory názvů a moduly.
ms.date: 06/15/2018
ms.openlocfilehash: c04ac8bf4ee360a2caa15be8f2bbea41105bd160
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627151"
---
# <a name="signatures"></a>Podpisy

Podpisový soubor obsahuje informace o veřejných podpisech sady prvků F# programu, jako jsou typy, obory názvů a moduly. Dá se použít k určení přístupnosti těchto prvků programu.

## <a name="remarks"></a>Poznámky

Pro každý F# soubor kódu můžete mít *soubor signatury*, což je soubor, který má stejný název jako soubor kódu, ale s příponou. fsi namísto. FS. Soubory signatur lze také přidat do příkazového řádku kompilace, pokud používáte příkazový řádek přímo. Aby bylo možné rozlišovat soubory kódu a soubory signatur, soubory kódu jsou někdy označovány jako *implementační soubory*. V projektu by měl soubor podpisu předcházet přidruženému souboru kódu.

Soubor signatury popisuje obory názvů, moduly, typy a členy v příslušném implementačním souboru. Informace v souboru signatury můžete použít k určení, které části kódu v příslušném implementačním souboru jsou k dispozici z kódu mimo implementační soubor a které části jsou interní pro implementační soubor. Obory názvů, moduly a typy, které jsou součástí souboru signatury, musí být podmnožinou oborů názvů, modulů a typů, které jsou součástí implementačního souboru. S některými výjimkami, které jsou uvedeny dále v tomto tématu, jsou tyto prvky jazyka, které nejsou uvedeny v souboru signatury, považovány za soukromé pro implementační soubor. Pokud se v projektu nebo příkazovém řádku nenalezne žádný soubor s podpisem, použije se výchozí přístupnost.

Další informace o výchozím usnadnění najdete v tématu [Access Control](access-control.md).

V souboru signatury neopakujete definici typů a implementací každé metody nebo funkce. Místo toho použijte signaturu pro každou metodu a funkci, která funguje jako kompletní specifikace funkcí, které jsou implementovány pomocí modulu nebo fragmentu oboru názvů. Syntaxe pro podpis typu je stejná jako ta, která se používá v deklaracích abstraktních metod v rozhraních a abstraktních třídách, a je zobrazena také F# pomocí technologie IntelliSense a překladače FSI. exe, když zobrazuje správně kompilovaný vstup.

Pokud není k dispozici dostatek informací v signatuře typu k určení, zda je typ zapečetěn nebo zda se jedná o typ rozhraní, je nutné přidat atribut, který označuje povahu typu kompilátoru. Atributy, které pro tento účel použijete, jsou popsány v následující tabulce.

|Atribut|Popis|
|---------|-----------|
|`[<Sealed>]`|Pro typ, který nemá žádné abstraktní členy nebo by neměl být rozšířen.|
|`[<Interface>]`|Pro typ, který je rozhraní.|

Kompilátor vytvoří chybu, pokud atributy nejsou konzistentní mezi signaturou a deklarací v implementačním souboru.

Pomocí klíčového `val` slova vytvořte podpis hodnoty nebo hodnoty funkce. Klíčové slovo `type` zavádí signaturu typu.

Podpisový soubor můžete vygenerovat pomocí `--sig` možnosti kompilátoru. Obecně není nutné zapisovat soubory. fsi ručně. Místo toho vygenerujete soubory. fsi pomocí kompilátoru, přidáte je do projektu, pokud ho máte, a upravíte je odebráním metod a funkcí, které nechcete zpřístupnit.

K dispozici je několik pravidel pro signatury typů:

- Zkratky typu v implementačním souboru nesmí odpovídat typu bez zkratky v souboru signatury.

- Záznamy a rozlišené sjednocení musí zveřejnit buď všechna pole, nebo žádná z jejich polí a konstruktorů a pořadí v signatuře musí odpovídat pořadí v implementačním souboru. Třídy mohou odhalit některá, všechna nebo žádná z jejich polí a metod v signatuře.

- Třídy a struktury, které mají konstruktory, musí vystavit deklarace svých základních tříd `inherits` (deklarace). Třídy a struktury, které mají konstruktory, musí také vystavit všechny abstraktní metody a deklarace rozhraní.

- Typy rozhraní musí odhalit všechny metody a rozhraní.

Pravidla pro signatury hodnot jsou následující:

- Modifikátory pro přístupnost (`public`, `internal`a `inline` tak dále) a modifikátory a `mutable` v signatuře se musí shodovat s modifikátory v implementaci.

- Počet parametrů obecného typu (implicitně odvozený nebo explicitně deklarovaný) musí odpovídat a typy a omezení typu v parametrech obecného typu se musí shodovat.

- Pokud je `Literal` atribut použit, musí se nacházet v signatuře i v implementaci a stejná hodnota literálu musí být použita pro obojí.

- Vzor parametrů (označovaných také jako *aritou*) podpisů a implementací musí být konzistentní.

- Pokud se názvy parametrů v souboru signatury liší od odpovídajícího implementačního souboru, místo toho se použije název v souboru signatury, což může způsobit problémy při ladění nebo profilaci. Pokud chcete být upozorněni na taková neshody, povolte upozornění 3218 v souboru projektu nebo při vyvolání kompilátoru (viz část `--warnon` [Možnosti kompilátoru](compiler-options.md)).

Následující příklad kódu ukazuje příklad souboru signatury, který má obor názvů, modul, hodnotu funkce a signatury typu společně s příslušnými atributy. Zobrazuje také odpovídající implementační soubor.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9002.fs)]

Následující kód ukazuje implementační soubor.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9001.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Řízení přístupu](access-control.md)
- [Možnosti kompilátoru](compiler-options.md)
