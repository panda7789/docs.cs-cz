---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 265141f77f4a61a61414a07214830feaa8a1ab05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351344"
---
# <a name="private-protected-visual-basic"></a>Soukromé chráněné (Visual Basic)

Kombinací klíčového slova `Private Protected` je modifikátor přístupu ke členu. `Private Protected` člen je přístupný pro všechny členy v příslušné třídě, stejně jako typy odvozené z nadřazené třídy, ale pouze v případě, že jsou nalezeny ve svém obsahujícím sestavení.

Můžete zadat `Private Protected` pouze pro členy třídy; `Private Protected` nelze použít u členů struktury, protože struktury nelze dědit.

Modifikátor přístupu `Private Protected` je podporován Visual Basic 15,5 a novějším. Chcete-li jej použít, můžete přidat následující prvek do souboru Visual Basic projektu (\*. vbproj). Pokud je v systému nainstalovaná Visual Basic 15,5 nebo novější, umožní vám využít všechny jazykové funkce podporované nejnovější verzí Visual Basic kompilátoru:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Další informace najdete v tématu [nastavení jazykové verze Visual Basic](../../language-reference/configure-language-version.md).

> [!NOTE]
> V aplikaci Visual Studio vyberte nápovědu F1 pro `private protected` poskytuje nápovědu pro [privátní](private.md) nebo [chráněné](protected.md). Rozhraní IDE vybere jeden token pod kurzorem namísto složeného slova.

## <a name="rules"></a>Pravidla

- **Kontext deklarace** `Private Protected` lze použít pouze na úrovni třídy. To znamená, že kontext deklarace pro prvek `Protected` musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.

## <a name="behavior"></a>Chování

- **Úroveň přístupu.** Veškerý kód ve třídě má přístup k jeho prvkům. Kód v jakékoli třídě, která je odvozena od základní třídy a je obsažen ve stejném sestavení, má přístup ke všem prvkům `Private Protected` základní třídy. Nicméně kód v jakékoli třídě, která je odvozena od základní třídy a je obsažen v jiném sestavení, nemůže přistupovat k základní třídě `Private Protected` prvky.

- **Modifikátory přístupu.** Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*. Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

V těchto kontextech lze použít modifikátor `Private Protected`:

- [Příkaz třídy](../../../visual-basic/language-reference/statements/class-statement.md) vnořené třídy

- [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)

- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) pro delegáta vnořený ve třídě

- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md) pro výčet vnořený ve třídě

- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)

- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Příkaz rozhraní](../../../visual-basic/language-reference/statements/interface-statement.md) rozhraní vnořeného ve třídě

- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Příkaz struktury](../../../visual-basic/language-reference/statements/structure-statement.md) struktury vnořené ve třídě

- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Viz také:

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Protected Friend](./protected-friend.md)
- [Úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
