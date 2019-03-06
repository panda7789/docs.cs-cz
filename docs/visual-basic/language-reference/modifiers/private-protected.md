---
title: Private Protected. (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: fea43558ac0fe8181f2786b69f2621346d446b2e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376387"
---
# <a name="private-protected-visual-basic"></a>Private Protected. (Visual Basic)

`Private Protected` – Kombinace klíčových slov je modifikátor přístupu členu. A `Private Protected` člen je přístupný podle všech členů v jeho obsahující třídy, a typy odvozené od třídy obsahující, ale pouze v případě, že se nenachází v jeho obsahující sestavení.

Můžete zadat `Private Protected` pouze pro členy třídy; nelze použít `Private Protected` na členy struktury protože struktury nelze dědit.

`Private Protected` Modifikátor přístupu je podporován v jazyce Visual Basic 15.5 nebo novější. Jeho použití, můžete přidat následující prvek do projektu jazyka Visual Basic (\*.vbproj) souboru. Jak dlouho jako 15.5 jazyka Visual Basic nebo vyšší je nainstalovaný ve vašem systému, umožňuje využít výhod všech funkcí jazyka podporovaná modulem nejnovější verzi kompilátoru jazyka Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Další informace najdete v části [nastavení verze jazyka Visual Basic](../../language-reference/configure-language-version.md).

> [!NOTE]
> V sadě Visual Studio, že vyberete nápovědy klávesy F1 na `private protected` poskytuje nápovědu pro buď [privátní](private.md) nebo [chráněné](protected.md). Rozhraní IDE zvolí jeden token pod kurzor spíše než složené slovo.

## <a name="rules"></a>pravidla

- **Místní deklarace.** Můžete použít `Private Protected` pouze na úrovni třídy. To znamená, že deklarace kontext `Protected` elementu musí být třída a nemůže být zdrojový soubor, obor názvů, rozhraní, modul, struktury nebo proceduru.

## <a name="behavior"></a>Chování

- **Úroveň přístupu.** Veškerý kód ve třídě můžete přístup k jeho prvkům. Kód do třídy, která je odvozena ze základní třídy a je obsažený ve stejném sestavení můžete přistupovat ke všem `Private Protected` prvky základní třídy. Ale kód do třídy, která je odvozena ze základní třídy a je obsažen v jiném sestavení nelze získat přístup k základní třídy `Private Protected` elementy.

- **Modifikátory přístupu.** Klíčová slova, které určují úroveň přístupu se nazývají *modifikátorů přístupu*. Porovnání přístupu modifikátory přístupu najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

`Private Protected` Modifikátor lze použít v těchto kontextech:

- [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md) vnořené třídy

- [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)

- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md) delegáta vnořená v třídě.

- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md) výčtu vnořená v třídě.

- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)

- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md) rozhraní vnořená v třídě.

- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Struktury příkaz](../../../visual-basic/language-reference/statements/structure-statement.md) struktury vnořená v třídě.

- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Viz také:

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Protected Friend](./protected-friend.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
