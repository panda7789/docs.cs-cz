---
title: Uživatelský datový typ
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 99eeb4b619f6bb23d00f8e449de953d41843f714
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343870"
---
# <a name="user-defined-data-type"></a>Uživatelský datový typ

Obsahuje data ve formátu, který definujete. Příkaz `Structure` definuje formát.

Předchozí verze Visual Basic podporují uživatelsky definovaný typ (UDT). Aktuální verze rozbalí UDT do *struktury*. Struktura je zřetězení jednoho nebo více *členů* různých datových typů. Visual Basic zachází se strukturou jako s jednou jednotkou, i když ke svým členům můžete přistupovat také jednotlivě.

## <a name="remarks"></a>Poznámky

Definujte a použijte datový typ struktura, pokud potřebujete zkombinovat různé datové typy do jedné jednotky nebo když žádný z základních datových typů nevyhovuje vašim potřebám.

Výchozí hodnota datového typu struktury se skládá z kombinace výchozích hodnot každého z jeho členů.

## <a name="declaration-format"></a>Formát deklarace

Deklarace struktury začíná [příkazem Structure](../../../visual-basic/language-reference/statements/structure-statement.md) a končí příkazem `End Structure`. Příkaz `Structure` poskytuje název struktury, což je také identifikátor datového typu, ve kterém je struktura definovaná. Jiné části kódu mohou použít tento identifikátor k deklarování proměnných, parametrů a návratových hodnot funkce, které mají být typu dat této struktury.

Deklarace mezi příkazy `Structure` a `End Structure` definují členy struktury.

## <a name="member-access-levels"></a>Úrovně přístupu členů

Každý člen musíte deklarovat pomocí [příkazu Dim](../../../visual-basic/language-reference/statements/dim-statement.md) nebo příkazu, který určuje úroveň přístupu, jako je například [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md)nebo [Private](../../../visual-basic/language-reference/modifiers/private.md). Pokud použijete příkaz `Dim`, nastaví se výchozí úroveň přístupu na veřejné.

## <a name="programming-tips"></a>Tipy k programování

- **Spotřeba paměti.** Stejně jako u všech složených datových typů nemůžete bezpečně vypočítat celkovou spotřebu paměti struktury tím, že přidáváte dohromady jmenovité přidělení úložiště jeho členů. Navíc nemůžete bezpečně předpokládat, že pořadí úložiště v paměti je stejné jako vaše pořadí deklarace. Pokud potřebujete řídit rozložení úložiště struktury, můžete použít atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> u příkazu `Structure`.

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že uživatelsky definované typy v jiných prostředích nejsou kompatibilní s typy Visual Basic struktury.

- **Rozšiřující.** Neexistuje žádný automatický převod na nebo z žádného datového typu struktury. Operátory převodu můžete definovat ve své struktuře pomocí [příkazu operátoru](../../../visual-basic/language-reference/statements/operator-statement.md)a můžete deklarovat každý operátor převodu, který má být `Widening` nebo `Narrowing`.

- **Znaky typu.** Datové typy struktury nemají znak typu literálu ani znak typu identifikátoru.

- **Typ rozhraní.** V .NET Framework neexistuje žádný odpovídající typ. Všechny struktury dědí z třídy .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, ale žádná jednotlivá struktura neodpovídají <xref:System.ValueType?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující paradigma znázorňuje obrys deklarace struktury.

```vb
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a>Viz také:

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
