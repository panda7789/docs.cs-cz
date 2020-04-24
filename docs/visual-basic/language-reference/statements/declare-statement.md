---
title: Declare – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
ms.openlocfilehash: 9895709076634ce156ba9d1009f79ba7ddd2ba56
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646374"
---
# <a name="declare-statement"></a>Declare – příkaz

Deklaruje odkaz na postup implementovaný v externím souboru.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ]
' -or-
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]
```

## <a name="parts"></a>Součásti

|Označení|Definice|
|---|---|
|`attributelist`|Nepovinný parametr. Viz [Seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|Nepovinný parametr. Může to být jedna z následujících možností:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Chráněné](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Přítel](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Soukromé](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Chráněný přítel](../../language-reference/modifiers/protected-friend.md)<br />- [Soukromé chráněné](../../language-reference/modifiers/private-protected.md)<br /><br /> Viz [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Nepovinný parametr. Viz [Stíny](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`charsetmodifier`|Nepovinný parametr. Určuje informace o znakové sadě a hledání souborů. Může to být jedna z následujících možností:<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) (výchozí)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Automaticky](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|Volitelné, ale `Sub` `Function` buď nebo musí se objevit. Označuje, že externí postup nevrátí hodnotu.|
|`Function`|Volitelné, ale `Sub` `Function` buď nebo musí se objevit. Označuje, že externí postup vrátí hodnotu.|
|`name`|Povinná hodnota. Název tohoto externího odkazu. Další informace naleznete v tématu [Deklarované názvy prvků](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Povinná hodnota. Zavádí `Lib` klauzuli, která identifikuje externí soubor (DLL nebo prostředek kódu), který obsahuje externí postup.|
|`libname`|Povinná hodnota. Název souboru, který obsahuje deklarovaný postup.|
|`Alias`|Nepovinný parametr. Označuje, že deklarovaný postup nelze v jeho `name`souboru identifikovat podle názvu uvedeného v aplikaci . Jeho identifikaci `aliasname`zadáte v .|
|`aliasname`|Povinné, pokud `Alias` použijete klíčové slovo. Řetězec, který identifikuje postup jedním ze dvou způsobů:<br /><br /> Název vstupního bodu procedury v jeho`""`souboru, v uvozovkách ( )<br /><br /> -nebo-<br /><br /> Znak čísla`#`( ) následovaný celé číslo uvedením řadového čísla vstupního bodu postupu v jeho spisu|
|`parameterlist`|Povinné, pokud postup přebírá parametry. Viz [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).|
|`returntype`|Povinné, `Function` pokud `Option Strict` je `On`zadán a je . Datový typ hodnoty vrácené postupem.|

## <a name="remarks"></a>Poznámky

Někdy je třeba volat proceduru definovanou v souboru (například DLL nebo zdroj kódu) mimo projekt. Když toto provést, kompilátor jazyka nemá přístup k informacím, které potřebuje k volání procedury správně, například kde je umístěn postup, jak je identifikován, jeho volání sekvence a návratový typ a znaková sada řetězce, který používá. Příkaz `Declare` vytvoří odkaz na externí postup a poskytne tyto nezbytné informace.

Můžete použít `Declare` pouze na úrovni modulu. To znamená, že *kontext deklarace* pro externí odkaz musí být třída, struktura nebo modul a nemůže být zdrojový soubor, obor názvů, rozhraní, postup nebo blok. Další informace naleznete [v tématu Kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Externí odkazy výchozí [pro veřejný](../../../visual-basic/language-reference/modifiers/public.md) přístup. Můžete upravit jejich úrovně přístupu pomocí modifikátorů přístupu.

## <a name="rules"></a>Pravidla

- **Atributy.** Atributy můžete použít na externí odkaz. Všechny atributy, které použijete, mají vliv pouze v projektu, nikoli v externím souboru.

- **Modifikátory.** Externí procedury jsou implicitně [Shared](../../../visual-basic/language-reference/modifiers/shared.md). `Shared` Klíčové slovo nelze použít při deklarování externího odkazu a nelze změnit jeho sdílený stav.

  Externí procedura se nemůže účastnit přepsání, implementovat členy rozhraní nebo zpracovávat události. Proto nelze `Overrides`v `Overridable` `NotOverridable` `MustOverride` `Implements` `Handles` `Declare` příkazu použít klíčové slovo , , , , nebo .

- **Název externí procedury.** Není třeba přikládat tento externí odkaz stejný `name`název (v ) jako název vstupního`aliasname`bodu procedury v jeho externím souboru ( ). Klauzuli `Alias` můžete použít k určení názvu vstupního bodu. To může být užitečné, pokud externí postup má stejný název jako visual basic vyhrazené modifikátor nebo proměnné, procedury nebo jakýkoli jiný programovací prvek ve stejném oboru.

  > [!NOTE]
  > Názvy vstupních bodů ve většině knihoven DLL rozlišují malá a velká písmena.

- **Externí číslo procedury.** Případně můžete použít `Alias` klauzuli k určení řadového čísla vstupního bodu v tabulce exportu externího souboru. Chcete-li to `aliasname` provést, začněte`#`znakem čísla ( ). To může být užitečné, pokud libovolný znak v názvu externí procedury není povolen v jazyce Visual Basic nebo pokud externí soubor exportuje proceduru bez názvu.

## <a name="data-type-rules"></a>Pravidla datového typu

- **Datové typy parametrů.** Pokud `Option Strict` `On`je , je nutné zadat datový `parameterlist`typ každého parametru v . Může se jednalo o libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní. V `parameterlist`rámci aplikace `As` můžete použít klauzuli k určení datového typu argumentu, který má být předán každému parametru.

  > [!NOTE]
  > Pokud externí postup nebyl napsán pro rozhraní .NET Framework, je třeba dbát na to, aby datové typy odpovídaly. Například pokud deklarujete externí odkaz na proceduru jazyka 6.0 s parametrem `Integer` (16 bitů `Short` v `Declare` jazyce Visual Basic 6.0), je nutné určit odpovídající argument jako v příkazu, protože to je 16bitový celočíselný typ v jazyce Visual Basic. Podobně `Long` má jinou šířku dat v jazyce `Date` Visual Basic 6.0 a je implementována odlišně.

- **Návratový datový typ.** Pokud externí postup `Function` je `Option Strict` `On`a je , je nutné zadat datový typ hodnoty vrácené volající kód. Může se jednalo o libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní.

  > [!NOTE]
  > Kompilátor jazyka neověřuje, zda jsou datové typy kompatibilní s typy externího postupu. Pokud je neshoda, za běhu běžného jazyka <xref:System.Runtime.InteropServices.MarshalDirectiveException> generuje výjimku za běhu.

- **Výchozí datové typy.** Pokud `Option Strict` `Off` je a nezadáte datový typ parametru v `parameterlist`aplikaci , kompilátor jazyka převede odpovídající argument na datový typ [objektu](../../../visual-basic/language-reference/data-types/object-data-type.md). Podobně pokud nezadáte `returntype`, kompilátor přebírá návratový datový `Object`typ .

  > [!NOTE]
  > Vzhledem k tomu, že máte co do činění s externí procedury, které by mohly být napsány na jiné platformě, je nebezpečné, aby jakékoli předpoklady o datových typech nebo umožnit jejich výchozí. Je mnohem bezpečnější určit datový typ každého parametru a vrácené hodnoty, pokud existuje. To také zlepšuje čitelnost kódu.

## <a name="behavior"></a>Chování

- **Rozsah.** Externí odkaz je v oboru v celé své třídě, struktuře nebo modulu.

- **Životnost.** Externí odkaz má stejnou životnost jako třída, struktura nebo modul, ve kterém je deklarován.

- **Volání externí procedury.** Externí proceduru voláte stejným způsobem, jakým voláte proceduru `Function` nebo `Sub` proceduru – pomocí ve výrazu, pokud vrátí hodnotu, nebo jeho zadáním do [příkazu volání,](../../../visual-basic/language-reference/statements/call-statement.md) pokud nevrátí hodnotu.

  Předáte argumenty externí mu procedury `parameterlist` přesně `Declare` tak, jak je určeno v příkazu. Neberou v úvahu, jak byly parametry původně deklarovány v externím souboru. Podobně pokud je vrácená hodnota, použijte ji `returntype` přesně `Declare` tak, jak je určeno v příkazu.

- **Znakové sady.** Můžete určit, `charsetmodifier` jak visual basic by zařazování řetězce při volání externí procedury. Modifikátor `Ansi` přesměruje Visual Basic zařadit všechny `Unicode` řetězce na hodnoty ANSI a modifikátor přesměruje jej zařazovat všechny řetězce unicode hodnoty. Modifikátor `Auto` přesměruje jazyk Visual Basic na zařazování `name`řetězců `aliasname` podle pravidel rozhraní .NET Framework založených na externím odkazu nebo pokud je zadán. Výchozí hodnota je `Ansi`.

  `charsetmodifier`také určuje, jak by měl jazyk Visual Basic vyhledat externí postup v rámci externího souboru. `Ansi`a `Unicode` oba přímé Visual Basic vyhledat bez změny jeho název během hledání. `Auto`přesměruje visual basic k určení základní znakové sady platformy run-time a případně upravit název externí procedury, a to následovně:

  - Na platformě ANSI, například windows 95, windows 98 nebo windows millennium edition, nejprve vyhledejte externí postup bez změny názvu. Pokud se to nezdaří, přidejte "A" na konec názvu externí procedury a vyhledejte jej znovu.

  - Na platformě Unicode, například windows nt, windows 2000 nebo windows xp, nejprve vyhledejte externí postup bez změny názvu. Pokud se to nezdaří, přidejte "W" na konec názvu externí procedury a vyhledejte jej znovu.

- **Mechanismus.** Visual Basic používá mechanismus *vyvolání platformy* Rozhraní .NET Framework (PInvoke) k vyřešení a přístupu k externím procedurám. Příkaz `Declare` a <xref:System.Runtime.InteropServices.DllImportAttribute> třída oba použít tento mechanismus automaticky a nepotřebujete žádné znalosti PInvoke. Další informace naleznete [v tématu Návod: Volání oken Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Pokud externí procedura běží mimo clr (COMMON Language runtime), je *nespravovaný kód*. Při volání takového postupu, například funkce rozhraní API systému Windows nebo metody COM, můžete vystavit aplikaci bezpečnostním rizikům. Další informace naleznete [v tématu Zásady bezpečného kódování pro nespravovaný kód](https://docs.microsoft.com/previous-versions/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code).

## <a name="example"></a>Příklad

Následující příklad deklaruje `Function` externí odkaz na proceduru, která vrací aktuální uživatelské jméno. Potom volá externí `GetUserNameA` postup jako `getUser` součást postupu.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Příklad

Poskytuje <xref:System.Runtime.InteropServices.DllImportAttribute> alternativní způsob použití funkcí v nespravovaném kódu. Následující příklad deklaruje importovnou funkci bez použití příkazu. `Declare`

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Příkaz Call](../../../visual-basic/language-reference/statements/call-statement.md)
- [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
