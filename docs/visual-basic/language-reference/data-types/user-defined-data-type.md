---
title: Uživatelsky definovaný datový typ (Visual Basic)
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
ms.openlocfilehash: 76073037dcaac0e87bc8a352f3b438332d11d881
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630139"
---
# <a name="user-defined-data-type"></a>Uživatelský datový typ

Obsahuje data ve formátu, který definujete. `Structure` Příkaz definuje formát.

Předchozí verze Visual Basic podporují uživatelsky definovaný typ (UDT). Aktuální verze rozbalí UDT do *struktury*. Struktura je zřetězení jednoho nebo více *členů* různých datových typů. Visual Basic zachází se strukturou jako s jednou jednotkou, i když ke svým členům můžete přistupovat také jednotlivě.

## <a name="remarks"></a>Poznámky

Definujte a použijte datový typ struktura, pokud potřebujete zkombinovat různé datové typy do jedné jednotky nebo když žádný z základních datových typů nevyhovuje vašim potřebám.

Výchozí hodnota datového typu struktury se skládá z kombinace výchozích hodnot každého z jeho členů.

## <a name="declaration-format"></a>Formát deklarace

Deklarace struktury začíná [příkazem Structure](../../../visual-basic/language-reference/statements/structure-statement.md) a končí `End Structure` příkazem. `Structure` Příkaz poskytuje název struktury, což je také identifikátor datového typu, ve kterém je struktura definovaná. Jiné části kódu mohou použít tento identifikátor k deklarování proměnných, parametrů a návratových hodnot funkce, které mají být typu dat této struktury.

Deklarace mezi `Structure` příkazy a `End Structure` definují členy struktury.

## <a name="member-access-levels"></a>Úrovně přístupu členů

Každý člen musíte deklarovat pomocí [příkazu Dim](../../../visual-basic/language-reference/statements/dim-statement.md) nebo příkazu, který určuje úroveň přístupu, jako je například [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md)nebo [Private](../../../visual-basic/language-reference/modifiers/private.md). Pokud použijete `Dim` příkaz, nastaví se výchozí úroveň přístupu na veřejné.

## <a name="programming-tips"></a>Tipy k programování

- **Spotřeba paměti.** Stejně jako u všech složených datových typů nemůžete bezpečně vypočítat celkovou spotřebu paměti struktury tím, že přidáváte dohromady jmenovité přidělení úložiště jeho členů. Navíc nemůžete bezpečně předpokládat, že pořadí úložiště v paměti je stejné jako vaše pořadí deklarace. Pokud potřebujete řídit rozložení úložiště struktury, můžete použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut `Structure` na příkaz.

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že uživatelsky definované typy v jiných prostředích nejsou kompatibilní s typy Visual Basic struktury.

- **Rozšiřující.** Neexistuje žádný automatický převod na nebo z žádného datového typu struktury. Operátory převodu můžete definovat ve své struktuře pomocí [příkazu operátoru](../../../visual-basic/language-reference/statements/operator-statement.md)a každý operátor `Widening` převodu lze deklarovat jako nebo `Narrowing`.

- **Znaky typu.** Datové typy struktury nemají znak typu literálu ani znak typu identifikátoru.

- **Typ rozhraní.** V .NET Framework neexistuje žádný odpovídající typ. Všechny struktury dědí z třídy <xref:System.ValueType?displayProperty=nameWithType>.NET Framework, ale žádná z nich neodpovídá. <xref:System.ValueType?displayProperty=nameWithType>

## <a name="example"></a>Příklad

Následující paradigma znázorňuje obrys deklarace struktury.

```
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
