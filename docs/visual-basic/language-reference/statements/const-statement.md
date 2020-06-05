---
title: Const – příkaz
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 3b05d4067ef99e03df07d2c316c982051180d961
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382104"
---
# <a name="const-statement-visual-basic"></a>Const – příkaz (Visual Basic)

Deklaruje a definuje jednu nebo více konstant.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ]
Const constantlist
```

## <a name="parts"></a>Součásti

`attributelist`  
Nepovinný parametr. Seznam atributů, které se vztahují na všechny konstanty deklarované v tomto příkazu. Viz [seznam atributů](attribute-list.md) v lomených závorkách (" `<` " a " `>` ").

`accessmodifier`  
Nepovinný parametr. Toto použijte k určení, ke kterému kódu má přístup k těmto konstantám. Může být [Veřejná](../modifiers/public.md), [chráněná](../modifiers/protected.md), [Friend](../modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../modifiers/private.md)nebo [Private Protected](../modifiers/private-protected.md).

`Shadows`  
Nepovinný parametr. Použijte k předeklaraci a skrytí programovacího prvku v základní třídě. Viz [Shadows](../modifiers/shadows.md).

`constantlist`  
Povinná hodnota. Seznam konstant, které jsou deklarovány v tomto příkazu.

`constant` `[ ,` `constant` `... ]`

Každá `constant` z nich má následující syntaxi a části:

`constantname` `[ As` `datatype` `] =` `initializer`

|Část|Description|
|----------|-----------------|
|`constantname`|Povinná hodnota. Název konstanty. Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`datatype`|Požadováno v `Option Strict` případě `On` , že je. Datový typ konstanty.|
|`initializer`|Povinná hodnota. Výraz vyhodnocený v době kompilace a přiřazený konstantě|

## <a name="remarks"></a>Poznámky

Pokud máte hodnotu, která se ve vaší aplikaci nikdy nemění, můžete definovat pojmenovanou konstantu a použít ji místo hodnoty literálu. Název je snazší pamatovat než hodnota. Konstantu můžete definovat pouze jednou a použít ji na mnoha místech kódu. Pokud v novější verzi potřebujete znovu definovat hodnotu, `Const` je příkaz jediným místem, které potřebujete k provedení změny.

Můžete použít `Const` pouze v modulu nebo v úrovni procedury. To znamená, že *kontext deklarace* proměnné musí být třída, struktura, modul, procedura nebo blok a nemůže se jednat o zdrojový soubor, obor názvů nebo rozhraní. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).

Místní konstanty (uvnitř procedury) jako výchozí pro veřejný přístup a nemůžete použít žádné modifikátory přístupu. Konstanty členů třídy a modulu (mimo jakákoli procedura) výchozí pro privátní přístup a členské konstanty struktury jsou standardně přístupné pro veřejný přístup. Můžete upravit jejich úrovně přístupu modifikátory přístupu.

## <a name="rules"></a>Pravidla

- **Kontext deklarace** Konstanta deklarovaná na úrovni modulu, mimo jakoukoli proceduru, je *členská konstanta*; je členem třídy, struktury nebo modulu, který je deklaruje.

  Konstanta deklarovaná na úrovni procedury je *místní konstanta*; je místní pro proceduru nebo blok, který je deklaruje.

- **Atribut.** Atributy lze použít pouze pro členské konstanty, nikoli pro místní konstanty. Atribut přispívá k metadatům sestavení, která nejsou smysluplná pro dočasné úložiště, jako jsou například místní konstanty.

- **Modifikátory.** Ve výchozím nastavení jsou všechny konstanty `Shared` , `Static` a `ReadOnly` . Při deklaraci konstanty nemůžete použít žádná z těchto klíčových slov.

  Na úrovni procedury nemůžete použít `Shadows` ani žádné modifikátory přístupu k deklaraci místních konstant.

- **Několik konstant.** Můžete deklarovat několik konstant v rámci jednoho příkazu deklarace a určit tak `constantname` část pro každé z nich. Vícenásobné konstanty jsou odděleny čárkami.

## <a name="data-type-rules"></a>Pravidla datového typu

- **Datové typy.** `Const`Příkaz může deklarovat datový typ proměnné. Můžete zadat libovolný datový typ nebo název výčtu.

- **Výchozí typ** Pokud nezadáte `datatype` , konstanta převezme datový typ `initializer` . Pokud zadáte obojí `datatype` a `initializer` , datový typ `initializer` musí být převoditelné na `datatype` . V případě `datatype` `initializer` , že není k dispozici ani, je výchozím datovým typem `Object` .

- **Různé typy.** Pro `As` každou proměnnou, kterou deklarujete, můžete zadat různé typy dat pro různé konstanty. Nelze však deklarovat několik konstant, které mají být stejného typu pomocí `As` klauzule Common.

- **Operace.** Je nutné inicializovat hodnotu každé konstanty v `constantlist` . Použijete `initializer` k poskytnutí výrazu, který se má přiřadit konstantě. Výraz může být libovolná kombinace literálů, dalších konstant, které jsou již definovány, a členů výčtu, které jsou již definovány. K kombinování takových prvků lze použít aritmetické a logické operátory.

  V nástroji nelze použít proměnné nebo funkce `initializer` . Můžete však použít klíčová slova převodu, jako je `CByte` a `CShort` . Můžete také použít, `AscW` Pokud je volána s konstantou `String` nebo `Char` argumentem, protože lze vyhodnotit v době kompilace.

## <a name="behavior"></a>Chování

- **Oboru.** Místní konstanty jsou přístupné pouze v rámci jejich procedury nebo bloku. Konstanty členů jsou přístupné odkudkoli v rámci své třídy, struktury nebo modulu.

- **Vydal.** Kód mimo třídu, strukturu nebo modul musí kvalifikovat název členské konstanty s názvem této třídy, struktury nebo modulu. Kód mimo proceduru nebo blok nemůže odkazovat na žádné místní konstanty v rámci tohoto postupu nebo bloku.

## <a name="example"></a>Příklad

Následující příklad používá `Const` příkaz k deklaraci konstant pro použití namísto hodnot literálů.

[!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]

## <a name="example"></a>Příklad

Definujete-li konstantu s datovým typem `Object` , kompilátor Visual Basic poskytne typu `initializer` místo `Object` . V následujícím příkladu má konstanta běhový `naturalLogBase` typ `Decimal` .

[!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]

Předchozí příklad používá <xref:System.Type.ToString%2A> metodu u <xref:System.Type> objektu vráceného [operátorem GetType](../operators/gettype-operator.md), protože <xref:System.Type> nelze převést na `String` použití `CStr` .

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Enum – příkaz](enum-statement.md)
- [#Const direktiva](../directives/const-directive.md)
- [Dim – příkaz](dim-statement.md)
- [ReDim – příkaz](redim-statement.md)
- [Implicitní a explicitní převody](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Konstanty a výčty](../../programming-guide/language-features/constants-enums/index.md)
- [Konstanty a výčty](../constants-and-enumerations.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
