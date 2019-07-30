---
title: Obecné typy
description: Naučte se používat F# obecné funkce a typy, které umožňují psát kód, který pracuje s různými typy bez opakujícího se kódu.
ms.date: 05/16/2016
ms.openlocfilehash: 47eed0b8e074cfb591e6d8e2c382b9ea6a6e97f0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630614"
---
# <a name="generics"></a>Obecné typy

F#hodnoty funkcí, metody, vlastnosti a agregované typy, jako jsou třídy, záznamy a rozlišené sjednocení, mohou být *Obecné*. Obecné konstrukce obsahují alespoň jeden parametr typu, který je obvykle poskytován uživatelem obecné konstrukce. Obecné funkce a typy umožňují napsat kód, který pracuje s různými typy bez opakování kódu pro každý typ. Nastavení obecného kódu může být jednoduché v F#, protože často je váš kód implicitně odvozený, aby byl obecný pro odvození typu kompilátor a automatické generalizace.

## <a name="syntax"></a>Syntaxe

```fsharp
// Explicitly generic function.
let function-name<type-parameters> parameter-list =
function-body

// Explicitly generic method.
[ static ] member object-identifer.method-name<type-parameters> parameter-list [ return-type ] =
method-body

// Explicitly generic class, record, interface, structure,
// or discriminated union.
type type-name<type-parameters> type-definition
```

## <a name="remarks"></a>Poznámky

Deklarace explicitně generické funkce nebo typu je podobná jako u neobecné funkce nebo typu, s výjimkou specifikace (a použití) parametrů typu, v lomených závorkách za funkcí nebo názvem typu.

Deklarace jsou často implicitně Obecné. Pokud nezadáte úplný typ každého parametru, který se používá k vytvoření funkce nebo typu, kompilátor se pokusí odvodit typ každého parametru, hodnoty a proměnné z kódu, který zapíšete. Další informace naleznete v tématu [odvození typu](../type-inference.md). Pokud kód pro váš typ nebo funkci neomezí jinak typy parametrů, funkce nebo typ je implicitně obecný. Tento proces se nazývá *Automatická generalizace*. Existují určitá omezení pro automatické generalizace. Například pokud F# kompilátor nemůže odvodit typy pro obecnou konstrukci, kompilátor ohlásí chybu, která odkazuje na omezení nazývané *omezení hodnoty*. V takovém případě může být nutné přidat některé anotace typu. Další informace o automatické generalizaci a omezení hodnoty a o tom, jak změnit kód pro vyřešení problému, najdete v tématu [Automatická generalizace](automatic-generalization.md).

V předchozí syntaxi *typ – parametry* jsou čárkami oddělený seznam parametrů, které reprezentují neznámé typy, z nichž každá začíná jednoduchou uvozovkou, volitelně s klauzulí omezení, která ještě více omezuje typy, které mohou být použity pro daný typ. ukazatele. Syntaxi klauzulí omezení různých druhů a dalších informací o omezeních naleznete v tématu [omezení](constraints.md).

*Definice typu* v syntaxi je stejná jako definice typu pro typ, který není obecný. Obsahuje parametry konstruktoru pro typ `as` třídy, volitelnou klauzuli, symbol rovnosti, pole záznamu `inherit` , klauzuli, volby pro rozlišené sjednocení `let` a `do` vazby, definice členů, a cokoli jiného povolený v definici bez obecného typu.

Ostatní prvky syntaxe jsou stejné jako u neobecných funkcí a typů. Například *identifikátor objektu* je identifikátor, který představuje samotný nadřazený objekt.

Vlastnosti, pole a konstruktory nemohou být obecnější než nadřazený typ. Hodnoty v modulu také nemohou být obecné.

## <a name="implicitly-generic-constructs"></a>Implicitně obecné konstrukce

Když F# kompilátor odvodí typy ve vašem kódu, automaticky zpracuje všechny funkce, které mohou být obecné. Pokud zadáte typ explicitně, například typ parametru, zabráníte automatické generalizaci.

V následujícím příkladu `makeList` kódu je obecný, a to i v případě, že ani jeho parametry nejsou explicitně deklarovány jako obecné.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

Podpis funkce je odvozený `'a -> 'a -> 'a list`. Všimněte si `a` , `b` že a v tomto příkladu jsou odvozeny, aby měly stejný typ. Je to proto, že jsou zahrnuty v seznamu dohromady a všechny prvky seznamu musí být stejného typu.

Můžete také vytvořit obecné funkce pomocí syntaxe jednoduchých uvozovek v anotaci typu k označení toho, že typ parametru je obecný parametr typu. V následujícím kódu je obecný `function1` , protože jeho parametry jsou deklarovány tímto způsobem, jako parametry typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]

## <a name="explicitly-generic-constructs"></a>Explicitní obecné konstrukce

Můžete také vytvořit obecnou funkci tím, že explicitně deklarujete své parametry typu v lomených závorkách (`<type-parameter>`). Následující kód to znázorňuje.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]

## <a name="using-generic-constructs"></a>Použití obecných konstrukcí

Při použití obecných funkcí nebo metod nemusí být nutné zadat argumenty typu. Kompilátor používá odvození typu pro odvození příslušných argumentů typu. Pokud je stále nejednoznačnost, můžete zadat argumenty typu v lomených závorkách a rozdělit více argumentů typu čárkami.

Následující kód ukazuje použití funkcí, které jsou definovány v předchozích částech.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]

> [!NOTE]
> Existují dva způsoby, jak odkazovat na obecný typ podle názvu. Například `list<int>` a `int list` jsou dva způsoby, jak odkazovat na obecný typ `list` , který má jeden argument `int`typu. Druhá forma je použita v konvenci pouze s vestavěnými F# typy, jako jsou `list` a. `option` Pokud existuje více argumentů typu, obvykle používáte syntaxi `Dictionary<int, string>` , ale můžete také použít syntaxi. `(int, string) Dictionary`

## <a name="wildcards-as-type-arguments"></a>Zástupné znaky jako argumenty typu

Chcete-li určit, že by měl být argument typu odvozen kompilátorem, lze použít podtržítko nebo zástupný symbol (`_`) namísto pojmenovaného argumentu typu. Tento kód je zobrazen v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]

## <a name="constraints-in-generic-types-and-functions"></a>Omezení v obecných typech a funkcích

V definici obecného typu nebo funkce můžete použít pouze ty konstrukce, které jsou známy k dispozici v parametru obecného typu. To je nutné k povolení ověřování volání funkcí a metod v době kompilace. Deklarujete-li parametry typu explicitně, můžete použít explicitní omezení na parametr obecného typu pro oznamování kompilátoru, že jsou k dispozici určité metody a funkce. Nicméně, pokud povolíte F# kompilátoru odvodit vaše obecné typy parametrů, určí příslušné omezení pro vás. Další informace najdete v tématu [omezení](constraints.md).

## <a name="statically-resolved-type-parameters"></a>Statisticky vyřešené parametry typu

Existují dva druhy parametrů typu, které lze použít v F# programech. První jsou parametry obecného typu pro typ popsaný v předchozích částech. Tento první druh parametru typu je ekvivalentní k parametrům obecného typu, které jsou používány v jazycích, jako je například C#Visual Basic a. Jiný typ parametru je specifický pro F# a je označován jako *staticky vyřešený parametr typu*. Informace o těchto konstrukcích naleznete v tématu [staticky vyřešené parametry typu](statically-resolved-type-parameters.md).

## <a name="examples"></a>Příklady

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka](../index.md)
- [Typy](../fsharp-types.md)
- [Statisticky vyřešené parametry typu](statically-resolved-type-parameters.md)
- [Obecné typy v .NET Framework](~/docs/standard/generics/index.md)
- [Automatická generalizace](automatic-generalization.md)
- [Omezení](constraints.md)
