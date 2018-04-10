---
title: Obecné typy (F#)
description: 'Další informace o použití F # obecné funkce a typy, které vám umožní napsat kód, který funguje s různými typy bez opakování kódu.'
keywords: 'Visual f #, f #, funkční programování'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a9f2e2ee-bcb1-4ce3-8531-850aa183040f
ms.openlocfilehash: e7a5712fddf4d372d1ada86927f50e394a59a410
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="generics"></a>Obecné typy

Funkce F # hodnoty, metody, vlastnosti a typy agregace, jako jsou třídy, zaznamenává a může být rozlišovaná sjednocení *Obecné*. Obecné konstrukce obsahovat alespoň jeden parametr typu, který je obvykle zadaný uživatelem obecné konstrukce. Obecné funkce a typy umožňují napsat kód, který funguje s různými typy bez opakování kód pro každý typ. Vytváření kódu Obecné může být jednoduchý v F #, protože často kódu je implicitně odvodit jako obecný odvození typu kompilátoru a Automatická generalizace mechanismy.


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
Prohlášení explicitně obecné funkce nebo typu mnohem je třeba u funkce neobecnou nebo typu, s výjimkou specifikace (a použití) parametry typu, v lomených závorkách po název funkce nebo typu.

Deklarace jsou často implicitně Obecné. Pokud nezadáte plně typ každý parametr, který se používá k vytvoření funkce nebo typu, pokusí se kompilátor odvození typu každý parametr, hodnoty a proměnné z kódu, kterou píšete. Další informace najdete v tématu [odvození typu](../type-inference.md). Pokud kód pro typ nebo funkci jinak neuvádělo typy parametrů, je implicitně obecné funkce nebo typu. Tento proces se nazývá *Automatická generalizace*. Existují některá omezení na automatická generalizace. Například pokud kompilátor jazyka F # se nepodařilo odvodit typy pro obecné konstrukce, kompilátor ohlásí chybu, která odkazuje na omezení volat *hodnoty omezení*. V takovém případě budete muset přidat některé typu poznámky. Další informace o Automatická Generalizace a omezení hodnoty a jak změnit svůj kód potíže vyřešit, najdete v části [Automatická generalizace](automatic-generalization.md).

V předchozích syntaxi *parametry typu* je textový soubor s oddělovači seznam parametrů, které představují neznámé typy, z nichž každá začíná jednoduché uvozovky, volitelně s klauzulí omezení, která další omezuje, co může typy použít pro tento parametr typu. Syntaxe pro omezení klauzulích různé typy a další informace o omezení, najdete v části [omezení](constraints.md).

*Definice typu* v syntaxi je stejná jako definice typu pro neobecný typ. Obsahuje parametry konstruktor pro typ třídy, volitelný `as` klauzule, rovnou symbol, pole záznamu `inherit` klauzule, volby rozlišovaná sjednocení `let` a `do` vazby, definice člena a jakékoli jiné definice typu neobecnou povoleny.

Další prvky syntaxe jsou stejné jako u neobecnou funkcí a typů. Například *identifikátor objektu* je identifikátor, který představuje obsahující odkaz sám na sebe.

Konstruktory, vlastnosti a pole nemůže být více obecné než nadřazených typů. Hodnoty v modulu také nemohou být obecný.


## <a name="implicitly-generic-constructs"></a>Implicitně obecné konstrukce
Když kompilátor jazyka F # odvodí, že typy v kódu, automaticky zpracovává všechny funkce, která může být obecný jako obecný. Pokud zadáte typu explicitně, jako je například typ parametru, abyste zabránili Automatická generalizace.

V následujícím příkladu kódu `makeList` je obecný, i když ho ani jeho parametry jsou deklarovány explicitně jako obecný.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

Podpis funkce je odvodit být `'a -> 'a -> 'a list`. Všimněte si, že `a` a `b` v tomto příkladu jsou odvodit tak, aby měl stejného typu. Je to proto, že jsou zahrnuty do seznamu společně a všechny elementy v seznamu musí být stejného typu.

Můžete provést také funkci obecné pomocí syntaxe jednoduché uvozovky v anotaci typu k označení, že je typ parametru parametr obecného typu. V následujícím kódu `function1` je obecný, protože jeho parametry jsou deklarovány tímto způsobem, jako parametrů typů.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]
    
## <a name="explicitly-generic-constructs"></a>Explicitně obecné konstrukce
Můžete provést také funkci obecné explicitně deklarováním jeho parametry typu v lomených závorkách (`<type-parameter>`). Následující kód to znázorňuje.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]
    
## <a name="using-generic-constructs"></a>Pomocí obecné konstrukce
Při použití obecné funkce nebo metod, nemusí mít k určení argumenty typu. Kompilátor používá odvození typu k odvození argumenty příslušného typu. Pokud je stále to nejednoznačnost, můžete zadat argumenty typu v lomených závorkách více argumentů typu oddělíte čárkami.

Následující kód ukazuje použití funkce, které jsou definované v předchozích částech.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]
    
>[!NOTE]
Existují dva způsoby, který bude odkazovat na obecného typu podle názvu. Například `list<int>` a `int list` jsou dva způsoby, jak odkazovat na obecného typu `list` s argumentem jednoho typu `int`. Druhé formuláře se obvykle používá jenom s předdefinovaných typů F #, jako `list` a `option`. Pokud existují více argumentů typu, je obvykle použít syntaxi `Dictionary<int, string>` ale můžete také použít syntaxi `(int, string) Dictionary`.

## <a name="wildcards-as-type-arguments"></a>Zástupné znaky jako argumenty typů
Chcete-li určit, že argument typu událostmi kompilátorem, můžete použít podtržítko nebo zástupný znak (`_`), místo argument pojmenovaného typu. To je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]
    
## <a name="constraints-in-generic-types-and-functions"></a>Omezení v obecné typy a funkce
V obecného typu nebo definice funkce můžete použít pouze konstrukce, která jsou známá, mají být k dispozici na parametr obecného typu. To je potřeba povolit ověření volání funkce a metoda v době kompilace. Pokud je výslovně deklarovat parametry typu, můžete použít explicitní omezení pro parametr obecného typu oznámit kompilátor některé metody a funkce jsou k dispozici. Ale pokud povolíte kompilátoru F # odvodit vaší obecný parametr typy, zjišťuje odpovídající omezení pro vás. Další informace najdete v tématu [omezení](constraints.md).


## <a name="statically-resolved-type-parameters"></a>Statisticky vyřešené parametry typu
Existují dva typy parametrů typu, které mohou být používány programů F #. První jsou parametry obecného typu druhu popsané v předchozích částech. Tento první druh parametr typu je stejná jako parametry obecného typu, které se používají v jazycích, jako je například Visual Basic a C#. Jiný druh parametr typu je specifický pro F # a odkazuje jako *parametr typu určené statisticky*. Informace o těchto konstrukce najdete v tématu [statisticky vyřešené parametry typu](statically-resolved-type-parameters.md).


## <a name="examples"></a>Příklady
[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]
    
## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka](../index.md)

[Typy](../fsharp-types.md)

[Statisticky vyřešené parametry typu](statically-resolved-type-parameters.md)

[Obecné typy v rozhraní .NET Framework](~/docs/standard/generics/index.md)

[Automatická generalizace](automatic-generalization.md)

[Omezení](constraints.md)
