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
ms.openlocfilehash: 021805508a8a053ccc8fab6f1013109bece4b6f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404768"
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

|Pojem|Definice|
|---|---|
|`attributelist`|Nepovinný parametr. Viz [seznam atributů](attribute-list.md).|
|`accessmodifier`|Nepovinný parametr. Může to být jedna z následujících:<br /><br /> -   [Republik](../modifiers/public.md)<br />-   [Proti](../modifiers/protected.md)<br />-   [Friend](../modifiers/friend.md)<br />-   [Hlášen](../modifiers/private.md)<br />- [Chráněný přítel](../modifiers/protected-friend.md)<br />- [Soukromé chráněné](../modifiers/private-protected.md)<br /><br /> Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Nepovinný parametr. Viz [Shadows](../modifiers/shadows.md).|
|`charsetmodifier`|Nepovinný parametr. Určuje znakovou sadu a informace o hledání souborů. Může to být jedna z následujících:<br /><br /> -   [ANSI](../modifiers/ansi.md) (výchozí)<br />-   [Sady](../modifiers/unicode.md)<br />-   [Automaticky](../modifiers/auto.md)|
|`Sub`|Volitelné, ale `Sub` `Function` musí být buď nebo. Indikuje, že externí procedura nevrací hodnotu.|
|`Function`|Volitelné, ale `Sub` `Function` musí být buď nebo. Označuje, že externí procedura vrací hodnotu.|
|`name`|Povinná hodnota. Název tohoto externího odkazu Další informace naleznete v tématu [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Povinná hodnota. Zavádí `Lib` klauzuli, která identifikuje externí soubor (DLL nebo prostředek kódu) obsahující externí proceduru.|
|`libname`|Povinná hodnota. Název souboru, který obsahuje deklarovanou proceduru.|
|`Alias`|Nepovinný parametr. Označuje, že procedura, kterou deklarujete, nemůže být v rámci svého souboru identifikována názvem zadaným v `name` . Určíte jeho identifikaci v `aliasname` .|
|`aliasname`|Vyžaduje se, pokud použijete `Alias` klíčové slovo. Řetězec, který identifikuje proceduru jedním ze dvou způsobů:<br /><br /> Název vstupního bodu procedury v rámci jeho souboru v uvozovkách ( `""` )<br /><br /> -nebo-<br /><br /> Znak čísla ( `#` ) následovaný celým číslem udávajícím pořadové číslo vstupního bodu procedury v rámci jeho souboru|
|`parameterlist`|Vyžaduje se, pokud procedura převezme parametry. Viz [seznam parametrů](parameter-list.md).|
|`returntype`|Požadováno `Function` , pokud je zadáno a `Option Strict` je `On` . Datový typ hodnoty vrácené procedurou|

## <a name="remarks"></a>Poznámky

Někdy je nutné volat proceduru definovanou v souboru (například knihovna DLL nebo prostředek kódu) mimo váš projekt. Pokud to uděláte, kompilátor Visual Basic nemá přístup k informacím, které potřebuje k správnému volání procedury, jako je například kde je procedura umístěna, jak je identifikována, její volající sekvence a návratový typ a znaková sada, kterou používá. `Declare`Příkaz vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.

Můžete použít `Declare` pouze na úrovni modulu. To znamená, že *kontext deklarace* pro externí odkaz musí být třída, struktura nebo modul a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, proceduru nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).

Externí odkazy jsou výchozí pro [veřejný](../modifiers/public.md) přístup. Můžete upravit jejich úrovně přístupu modifikátory přístupu.

## <a name="rules"></a>Pravidla

- **Atribut.** Můžete použít atributy na externí odkaz. Libovolný atribut, který použijete, má vliv pouze na projekt, nikoli v externím souboru.

- **Modifikátory.** Externí procedury jsou implicitně [sdíleny](../modifiers/shared.md). Klíčové slovo nelze použít `Shared` při deklaraci externího odkazu a nelze změnit jeho sdílený stav.

  Externí procedura se nemůže zúčastnit přepsání, implementace členů rozhraní nebo zpracování událostí. V příkazu proto nelze použít `Overrides` `Overridable` `NotOverridable` klíčové slovo,,, `MustOverride` , `Implements` nebo `Handles` `Declare` .

- **Název externí procedury** Tento externí odkaz není nutné zadávat na stejný název (v `name` ) jako název vstupního bodu procedury v jeho externím souboru ( `aliasname` ). `Alias`K určení názvu vstupního bodu můžete použít klauzuli. To může být užitečné v případě, že externí procedura má stejný název jako Visual Basic rezervovaný modifikátor nebo proměnná, procedura nebo jakýkoli jiný programový prvek ve stejném oboru.

  > [!NOTE]
  > Názvy vstupních bodů ve většině knihoven DLL rozlišují velká a malá písmena.

- **Externí číslo procedury** Alternativně můžete pomocí `Alias` klauzule zadat pořadové číslo vstupního bodu v tabulce exportu externího souboru. K tomu je třeba začínat `aliasname` znakem čísla ( `#` ). To může být užitečné, pokud libovolný znak v názvu externí procedury není povolen v Visual Basic, nebo pokud externí soubor exportuje proceduru bez názvu.

## <a name="data-type-rules"></a>Pravidla datového typu

- **Datové typy parametrů.** Pokud `Option Strict` je `On` , je nutné zadat datový typ každého parametru v `parameterlist` . Může to být libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní. V rámci `parameterlist` použijte `As` klauzuli k určení datového typu argumentu, který má být předán každému parametru.

  > [!NOTE]
  > Pokud externí procedura nebyla zapsána pro .NET Framework, je nutné dbát na to, aby datové typy odpovídaly. Například pokud deklarujete externí odkaz na Visual Basic 6,0 s `Integer` parametrem (16 bitů v Visual Basic 6,0), je nutné určit odpovídající argument jako `Short` v `Declare` příkazu, protože to je 16bitový typ integer v Visual Basic. Podobně `Long` má odlišnou šířku dat v Visual Basic 6,0 a `Date` je implementována jinak.

- **Návratový typ dat** Pokud je externí procedura `Function` a, je `Option Strict` `On` nutné zadat datový typ hodnoty vrácené volajícímu kódu. Může to být libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní.

  > [!NOTE]
  > Kompilátor Visual Basic neověřuje, zda jsou datové typy kompatibilní s externí procedurou. Pokud dojde k neshodě, modul CLR (Common Language Runtime) vygeneruje <xref:System.Runtime.InteropServices.MarshalDirectiveException> v době běhu výjimku.

- **Výchozí datové typy.** Pokud `Option Strict` je `Off` a neurčíte datový typ parametru v `parameterlist` , kompilátor Visual Basic převede odpovídající argument na [datový typ objektu](../data-types/object-data-type.md). Podobně pokud nezadáte `returntype` , kompilátor převezme návratový datový typ `Object` .

  > [!NOTE]
  > Vzhledem k tomu, že pracujete s externí procedurou, která mohla být napsána na jiné platformě, je nebezpečné dělat jakékoli předpoklady týkající se datových typů nebo jim umožnit jejich výchozí nastavení. Je mnohem bezpečnější zadat datový typ každého parametru a vrácenou hodnotu, pokud existuje. Tím se také zlepšuje čitelnost kódu.

## <a name="behavior"></a>Chování

- **Oboru.** Externí odkaz je v rozsahu v rámci své třídy, struktury nebo modulu.

- **Platné.** Externí odkaz má stejnou životnost jako třída, struktura nebo modul, ve kterém je deklarována.

- **Volání externí procedury.** Externí proceduru zavoláte stejným způsobem jako `Function` `Sub` proceduru nebo – jejich použitím ve výrazu, pokud vrátí hodnotu, nebo zadáním v [příkazu volání](call-statement.md) , pokud nevrátí hodnotu.

  Předáváte argumenty externí proceduře přesně tak, jak `parameterlist` je uvedeno v `Declare` příkazu. Neberou v úvahu způsob, jakým byly parametry původně deklarovány v externím souboru. Podobně, pokud existuje návratová hodnota, použijte ji přesně tak, jak je uvedeno `returntype` v `Declare` příkazu.

- **Znakové sady.** Můžete určit, `charsetmodifier` jak má Visual Basic při volání externí procedury zařazovat řetězce. `Ansi`Modifikátor přesměruje Visual Basic k zařazení všech řetězců do hodnot ANSI a `Unicode` Modifikátor ho přesměruje na zařazování všech řetězců do hodnot Unicode. `Auto`Modifikátor směruje Visual Basic zařazování řetězců podle .NET Framework pravidel založených na externím odkazu `name` , nebo je- `aliasname` li tento parametr zadán. Výchozí hodnota je `Ansi`.

  `charsetmodifier`Určuje také, jak má Visual Basic Hledat externí postup v rámci jeho externího souboru. `Ansi`a `Unicode` přímá Visual Basic k jejímu vyhledání bez změny názvu během hledání. `Auto`směruje Visual Basic k určení základní znakové sady běhové platformy a případně upraví název externí procedury následujícím způsobem:

  - Na platformě ANSI, jako je Windows 95, Windows 98 nebo Windows Millennium Edition, nejprve vyhledáte externí postup beze změny názvu. V případě neúspěšného pokusu připojit "A" k konci názvu externí procedury a znovu ho vyhledat.

  - Na platformě Unicode, jako je Windows NT, Windows 2000 nebo Windows XP, nejprve vyhledáte externí postup beze změny názvu. Pokud se to nezdaří, přidejte "W" na konec názvu externí procedury a znovu ho vyhledejte.

- **Mechanismy.** Visual Basic používá mechanismus *volání .NET Framework platformy* (PInvoke) pro řešení a přístup k externím procedurám. `Declare`Příkaz a <xref:System.Runtime.InteropServices.DllImportAttribute> Třída používají tento mechanismus automaticky a nepotřebujete žádné znalosti PInvoke. Další informace najdete v tématu [Návod: volání rozhraní API systému Windows](../../programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Pokud externí procedura běží mimo modul CLR (Common Language Runtime), jedná se o *nespravovaný kód*. Když zavoláte takovou proceduru, například funkci rozhraní Windows API nebo metodu COM, můžete svou aplikaci vystavit bezpečnostním rizikům. Další informace najdete v tématu [pokyny k zabezpečenému kódování pro nespravovaný kód](https://docs.microsoft.com/previous-versions/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code).

## <a name="example"></a>Příklad

Následující příklad deklaruje externí odkaz na `Function` proceduru, která vrací aktuální uživatelské jméno. Pak volá externí proceduru `GetUserNameA` jako součást `getUser` procedury.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Příklad

<xref:System.Runtime.InteropServices.DllImportAttribute>Poskytuje alternativní způsob používání funkcí v nespravovaném kódu. Následující příklad deklaruje importovanou funkci bez použití `Declare` příkazu.

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports – příkaz (obor názvů a typ rozhraní .NET)](imports-statement-net-namespace-and-type.md)
- [AddressOf – operátor](../operators/addressof-operator.md)
- [Function – příkaz](function-statement.md)
- [Sub – příkaz](sub-statement.md)
- [Seznam parametrů](parameter-list.md)
- [Call – příkaz](call-statement.md)
- [Návod: Volání rozhraní API systému Windows](../../programming-guide/com-interop/walkthrough-calling-windows-apis.md)
