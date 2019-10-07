---
title: Declare – příkaz (Visual Basic)
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
ms.openlocfilehash: e839fe14c360229fbe0350fd7878c7a844056e8b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005089"
---
# <a name="declare-statement"></a>Declare – příkaz

Deklaruje odkaz na proceduru implementovanou v externím souboru.

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

|Termín|Definice|
|---|---|
|`attributelist`|Volitelné. Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|Volitelné. Může to být jedna z následujících:<br /><br /> @no__t – 0[veřejných](../../../visual-basic/language-reference/modifiers/public.md)<br />[chráněný](../../../visual-basic/language-reference/modifiers/protected.md) @no__t – 0<br />-    –[přítel](../../../visual-basic/language-reference/modifiers/friend.md)<br />@no__t – 0[privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />[přítel chráněný](../../language-reference/modifiers/protected-friend.md) @no__t – 0<br />- [Private Protected](../../language-reference/modifiers/private-protected.md)<br /><br /> Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Volitelné. Viz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`charsetmodifier`|Volitelné. Určuje znakovou sadu a informace o hledání souborů. Může to být jedna z následujících:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (výchozí)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />@no__t – 0[auto](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|Volitelné, ale musí se zobrazit buď `Sub`, nebo `Function`. Indikuje, že externí procedura nevrací hodnotu.|
|`Function`|Volitelné, ale musí se zobrazit buď `Sub`, nebo `Function`. Označuje, že externí procedura vrací hodnotu.|
|`name`|Požadováno. Název tohoto externího odkazu Další informace naleznete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Požadováno. Zavádí klauzuli `Lib`, která identifikuje externí soubor (knihovna DLL nebo prostředek kódu) obsahující externí proceduru.|
|`libname`|Požadováno. Název souboru, který obsahuje deklarovanou proceduru.|
|`Alias`|Volitelné. Označuje, že procedura, kterou deklarujete, nelze v rámci svého souboru identifikovat pomocí názvu zadaného v `name`. Určíte jeho identifikaci v `aliasname`.|
|`aliasname`|Vyžaduje se, pokud použijete klíčové slovo `Alias`. Řetězec, který identifikuje proceduru jedním ze dvou způsobů:<br /><br /> Název vstupního bodu procedury v souboru, v rámci uvozovek (`""`)<br /><br /> -nebo-<br /><br /> Znak čísla (`#`) následovaný celým číslem určujícím pořadové číslo vstupního bodu procedury v rámci jeho souboru|
|`parameterlist`|Vyžaduje se, pokud procedura převezme parametry. Viz [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).|
|`returntype`|Požadováno, pokud je zadána hodnota `Function` a `Option Strict` je `On`. Datový typ hodnoty vrácené procedurou|

## <a name="remarks"></a>Poznámky

Někdy je nutné volat proceduru definovanou v souboru (například knihovna DLL nebo prostředek kódu) mimo váš projekt. Pokud to uděláte, kompilátor Visual Basic nemá přístup k informacím, které potřebuje k správnému volání procedury, jako je například kde je procedura umístěna, jak je identifikována, její volající sekvence a návratový typ a znaková sada, kterou používá. Příkaz `Declare` vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.

@No__t-0 můžete použít pouze na úrovni modulu. To znamená, že *kontext deklarace* pro externí odkaz musí být třída, struktura nebo modul a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, proceduru nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Externí odkazy jsou výchozí pro [veřejný](../../../visual-basic/language-reference/modifiers/public.md) přístup. Můžete upravit jejich úrovně přístupu modifikátory přístupu.

## <a name="rules"></a>Pravidly

- **Atribut.** Můžete použít atributy na externí odkaz. Libovolný atribut, který použijete, má vliv pouze na projekt, nikoli v externím souboru.

- **Modifikátory.** Externí procedury jsou implicitně [sdíleny](../../../visual-basic/language-reference/modifiers/shared.md). Při deklaraci externího odkazu nemůžete použít klíčové slovo `Shared` a nemůžete změnit jeho sdílený stav.

  Externí procedura se nemůže zúčastnit přepsání, implementace členů rozhraní nebo zpracování událostí. V příkazu `Declare` proto nelze použít klíčové slovo `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements` nebo `Handles`.

- **Název externí procedury** Tento externí odkaz není nutné zadávat na stejný název (v `name`) jako název vstupní bod v rámci jeho externího souboru (`aliasname`). Pomocí klauzule `Alias` můžete zadat název vstupního bodu. To může být užitečné v případě, že externí procedura má stejný název jako Visual Basic rezervovaný modifikátor nebo proměnná, procedura nebo jakýkoli jiný programový prvek ve stejném oboru.

  > [!NOTE]
  > Názvy vstupních bodů ve většině knihoven DLL rozlišují velká a malá písmena.

- **Externí číslo procedury** Alternativně můžete použít klauzuli `Alias` a zadat tak pořadové číslo vstupního bodu v exportní tabulce externího souboru. Chcete-li to provést, začněte `aliasname` s znakem čísla (`#`). To může být užitečné, pokud libovolný znak v názvu externí procedury není povolen v Visual Basic, nebo pokud externí soubor exportuje proceduru bez názvu.

## <a name="data-type-rules"></a>Pravidla datového typu

- **Datové typy parametrů.** Pokud je `Option Strict` `On`, je nutné zadat datový typ každého parametru v `parameterlist`. Může to být libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní. V rámci `parameterlist` použijete klauzuli `As` k určení datového typu argumentu, který se má předat jednotlivým parametrům.

  > [!NOTE]
  > Pokud externí procedura nebyla zapsána pro .NET Framework, je nutné dbát na to, aby datové typy odpovídaly. Například pokud deklarujete externí odkaz na Visual Basic 6,0 s parametrem `Integer` (16 bitů v Visual Basic 6,0), je nutné určit odpovídající argument jako `Short` v příkazu `Declare`, protože se jedná o 16bitový celočíselný typ v Visual Basic. Podobně `Long` má odlišnou šířku dat v Visual Basic 6,0 a `Date` je implementováno jinak.

- **Návratový typ dat** Pokud je externí procedura `Function` a `Option Strict` je `On`, je nutné zadat datový typ hodnoty vrácené volajícímu kódu. Může to být libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní.

  > [!NOTE]
  > Kompilátor Visual Basic neověřuje, zda jsou datové typy kompatibilní s externí procedurou. Pokud dojde k neshodě, modul CLR (Common Language Runtime) vygeneruje v době běhu výjimku <xref:System.Runtime.InteropServices.MarshalDirectiveException>.

- **Výchozí datové typy.** Pokud je `Option Strict` `Off` a neurčíte datový typ parametru v `parameterlist`, kompilátor Visual Basic převede odpovídající argument na [datový typ Object](../../../visual-basic/language-reference/data-types/object-data-type.md). Podobně pokud nezadáte `returntype`, kompilátor převezme typ vracených dat, který bude `Object`.

  > [!NOTE]
  > Vzhledem k tomu, že pracujete s externí procedurou, která mohla být napsána na jiné platformě, je nebezpečné dělat jakékoli předpoklady týkající se datových typů nebo jim umožnit jejich výchozí nastavení. Je mnohem bezpečnější zadat datový typ každého parametru a vrácenou hodnotu, pokud existuje. Tím se také zlepšuje čitelnost kódu.

## <a name="behavior"></a>Předvídatelně

- **Oboru.** Externí odkaz je v rozsahu v rámci své třídy, struktury nebo modulu.

- **Platné.** Externí odkaz má stejnou životnost jako třída, struktura nebo modul, ve kterém je deklarována.

- **Volání externí procedury.** Externí procedura se volá stejným způsobem jako `Function` nebo `Sub` – pomocí výrazu ve výrazu, pokud vrátí hodnotu nebo zadáním v [příkazu volání](../../../visual-basic/language-reference/statements/call-statement.md) , pokud nevrátí hodnotu.

  Do příkazu `Declare` předáte argumenty k externí proceduře přesně tak, jak je určeno `parameterlist`. Neberou v úvahu způsob, jakým byly parametry původně deklarovány v externím souboru. Podobně, pokud existuje návratová hodnota, použijte ji přesně tak, jak je určeno hodnotou `returntype` v příkazu `Declare`.

- **Znakové sady.** Můžete zadat v `charsetmodifier`, jak by měla Visual Basic zařazovat řetězce při volání externí procedury. Modifikátor `Ansi` přesměruje Visual Basic na zařazení všech řetězců do hodnot ANSI a modifikátor `Unicode` ho přesměruje na zařazení všech řetězců do hodnot Unicode. Modifikátor `Auto` přesměruje Visual Basic na zařazování řetězců podle .NET Framework pravidel založených na externích odkazech `name` nebo `aliasname`, pokud je zadaný. Výchozí hodnota je `Ansi`.

  `charsetmodifier` také určuje, jak má Visual Basic vyhledat externí postup v rámci svého externího souboru. `Ansi` a `Unicode` Přímá Visual Basic k jejímu vyhledání bez změny názvu během hledání. `Auto` přímé Visual Basic k určení základní znakové sady běhové platformy a případně upraví název externí procedury následujícím způsobem:

  - Na platformě ANSI, jako je Windows 95, Windows 98 nebo Windows Millennium Edition, nejprve vyhledáte externí postup beze změny názvu. V případě neúspěšného pokusu připojit "A" k konci názvu externí procedury a znovu ho vyhledat.

  - Na platformě Unicode, jako je Windows NT, Windows 2000 nebo Windows XP, nejprve vyhledáte externí postup beze změny názvu. Pokud se to nezdaří, přidejte "W" na konec názvu externí procedury a znovu ho vyhledejte.

- **Mechanismy.** Visual Basic používá mechanismus *volání .NET Framework platformy* (PInvoke) pro řešení a přístup k externím procedurám. Příkaz `Declare` a třída <xref:System.Runtime.InteropServices.DllImportAttribute> používají tento mechanismus automaticky a nepotřebujete žádné znalosti PInvoke. Další informace najdete v tématu [Návod: volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Pokud externí procedura běží mimo modul CLR (Common Language Runtime), jedná se o *nespravovaný kód*. Když zavoláte takovou proceduru, například funkci rozhraní Windows API nebo metodu COM, můžete svou aplikaci vystavit bezpečnostním rizikům. Další informace najdete v tématu [pokyny k zabezpečenému kódování pro nespravovaný kód](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).

## <a name="example"></a>Příklad

Následující příklad deklaruje externí odkaz na proceduru @no__t 0, která vrací aktuální uživatelské jméno. Pak zavolá externí proceduru `GetUserNameA` jako součást procedury `getUser`.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Příklad

@No__t-0 poskytuje alternativní způsob používání funkcí v nespravovaném kódu. Následující příklad deklaruje importovanou funkci bez použití příkazu `Declare`.

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Příkaz Call](../../../visual-basic/language-reference/statements/call-statement.md)
- [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
