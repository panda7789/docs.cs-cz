---
title: Obecné typy (F#)
description: 'Další informace o použití F # obecné funkce a typy, které umožňují také napsat kód, který funguje s různými typy bez opakující se kód.'
ms.date: 05/16/2016
ms.openlocfilehash: fc061f19c6c7fa737f7ca05aae83fd42c0010b37
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44084959"
---
# <a name="generics"></a>Obecné typy

Funkce jazyka F # hodnoty metody, vlastnosti a agregované typy, jako jsou třídy, záznamů a rozlišovaná sjednocení mohou být *obecný*. Obecné konstrukce obsahují alespoň jeden parametr typu, který je obvykle zadaný uživatelem obecného konstruktoru. Obecné funkce a typy umožňují napsat kód, který funguje s různými typy bez nutnosti opakovat pro každý typ kódu. Provádění kódu obecný může být jednoduché v jazyce F #, protože často kódu je implicitně odvozena jako obecný kompilátoru odvození typu a Automatická generalizace mechanismy.

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

Deklarace explicitně obecná funkce nebo typu je mnohem, neobecné funkce nebo typ, s výjimkou specifikace (a použití) parametry typu, v lomených závorkách za názvem funkce nebo typy.

Deklarace jsou často implicitně Obecné. Pokud nezadáte plně zadejte každý parametr, který se používá k vytvoření funkce nebo typ, kompilátor se pokusí odvodit typ každého parametru, hodnoty a proměnné z kódu, který napíšete. Další informace najdete v tématu [odvození typu](../type-inference.md). Pokud kód pro typ nebo funkce, v opačném případě neomezuje typy parametrů, je implicitně obecná funkce nebo typy. Tento proces se nazývá *Automatická generalizace*. Automatická generalizace existují některá omezení. Například pokud kompilátor F # nemůže odvodit typy parametrů obecného konstruktoru, kompilátor zobrazí chybová zpráva, která odkazuje na omezení, volá se, *hodnota omezení*. V takovém případě budete muset přidat některé poznámky typu. Další informace o Automatická Generalizace a omezení hodnoty a jak změnit váš kód k vyřešení problému najdete v tématu [Automatická generalizace](automatic-generalization.md).

V předchozí syntaxi *parametry typu* je čárkou oddělený seznam parametrů, které představují neznámé typy, z nichž každý začíná jednoduchou uvozovku, volitelně s klauzulí omezení, která dále omezuje, co může typy použít pro parametr typu. Syntaxe klauzule omezení různé typy a další informace o omezení, najdete v části [omezení](constraints.md).

*Definice typu* syntaxe je stejná jako definice typu jiného než obecného typu. Obsahuje parametry konstruktoru pro typ třídy, volitelně `as` klauzule, symbol rovná, pole záznamu `inherit` klauzule, možnosti pro diskriminované sjednocení, `let` a `do` vazby, definice členů a vše ostatní povoleny v definici typu Obecné.

Ostatní prvky syntaxe jsou stejné jako u neobecných funkcí a typů. Například *identifikátor objektu* je identifikátor, který představuje obsahující samotného objektu.

Vlastnosti, polí a konstruktorů nemůžou být obecnější než nadřazený typ. Navíc hodnoty v modulu nemohou být obecné.

## <a name="implicitly-generic-constructs"></a>Implicitně obecné konstrukce

Když kompilátor jazyka F # odvodí typy ve vašem kódu, automaticky zpracovává všechny funkce, které může být obecný jako obecný. Pokud zadáte typ explicitně, jako je například typ parametru, abyste zabránili Automatická generalizace.

V následujícím příkladu kódu `makeList` je obecný, i když ho ani její parametry jsou explicitně deklarována jako obecný.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

Signatura funkce odvozena jako `'a -> 'a -> 'a list`. Všimněte si, že `a` a `b` v tomto příkladu jsou odvozen, aby měl stejného typu. Je to proto, že v seznamu jsou zahrnuty společně a všechny prvky seznamu musí být stejného typu.

Můžete provést také funkce obecného pomocí jednoduché uvozovky syntaxe v anotaci typu k označení, že typ parametru je parametr obecného typu. V následujícím kódu `function1` je obecný, protože jeho parametry jsou deklarovány v tímto způsobem, jako parametry typu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]

## <a name="explicitly-generic-constructs"></a>Explicitně obecné konstrukce

Můžete provést také funkce obecného pomocí explicitní deklarace jeho parametrů typu v lomených závorkách (`<type-parameter>`). Následující kód to znázorňuje.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]

## <a name="using-generic-constructs"></a>Použití obecné konstrukce

Při použití obecné funkce nebo metody nemusí mít k určení argumentů typu. Odvození typu používá kompilátor k odvození příslušnými argumenty typu. Pokud stále existuje nejednoznačnost, můžete zadat argumenty typu v lomených závorkách, více argumentů typu oddělíte čárkami.

Následující kód ukazuje použití těchto funkcí, které jsou definovány v předchozích částech.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]

>[!NOTE]
Existují dva způsoby, jak odkazovat na obecný typ podle názvu. Například `list<int>` a `int list` jsou dva způsoby, jak odkazovat na obecný typ `list` , který má jako argument jeden typ `int`. Druhý formulář se obvykle používá jenom s předdefinovaných typů F #, jako `list` a `option`. Pokud existuje více argumentů typu, je obvykle použít syntaxi `Dictionary<int, string>` ale můžete také použít syntaxi `(int, string) Dictionary`.

## <a name="wildcards-as-type-arguments"></a>Zástupné znaky jako argumenty typu

Chcete-li určit, že by měl kompilátor odvodit argument typu, můžete použít znak podtržení nebo zástupný symbol (`_`), namísto argument s názvem typu. To je ukázáno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]

## <a name="constraints-in-generic-types-and-functions"></a>Omezení v obecné typy a funkce

V obecném typu nebo definici funkce můžete použít pouze konstrukce, které jsou známé jako k dispozici na parametr obecného typu. To se vyžaduje pro povolení ověření volání funkce a metody v době kompilace. Pokud explicitně deklarujete parametry typu, můžete provést explicitní omezení u obecného parametru typu upozornění kompilátoru, že některé metody a funkce jsou k dispozici. Ale pokud je povoleno kompilátor jazyka F # k odvození typů obecný parametr, určuje odpovídající omezení za vás. Další informace najdete v tématu [omezení](constraints.md).

## <a name="statically-resolved-type-parameters"></a>Statisticky vyřešené parametry typu

Existují dva typy parametrů typu, které lze použít v aplikacích F #. První jsou parametry obecného typu, typu je popsáno v předchozích částech. Tento typ prvního parametru typu je ekvivalentní parametrům obecného typu, které se používají v jazycích, jako je například Visual Basic a C#. Jiný typ parametru typu je specifická pro F # a se označuje jako *parametr staticky řešeného typu*. Informace o těchto konstruktorů najdete v tématu [statisticky vyřešených parametrů typu](statically-resolved-type-parameters.md).

## <a name="examples"></a>Příklady

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka](../index.md)
- [Typy](../fsharp-types.md)
- [Statisticky vyřešené parametry typu](statically-resolved-type-parameters.md)
- [Obecné typy v rozhraní .NET Framework](~/docs/standard/generics/index.md)
- [Automatická generalizace](automatic-generalization.md)
- [Omezení](constraints.md)
