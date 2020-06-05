---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: b7d9f81e41950b92c787e2e50fb94fe3d7c07559
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362226"
---
# <a name="private-protected-visual-basic"></a>Soukromé chráněné (Visual Basic)

`Private Protected`Kombinace klíčového slova je modifikátor přístupu ke členu. `Private Protected`Člen je přístupný pro všechny členy ve své nadřazené třídě a také podle typů odvozených z obsahující třídy, ale pouze v případě, že jsou nalezeny ve svém nadřazeném sestavení.

Můžete zadat `Private Protected` pouze členy tříd. nemůžete použít `Private Protected` pro členy struktury, protože struktury nelze dědit.

`Private Protected`Modifikátor přístupu je podporován Visual Basic 15,5 a novějším. Chcete-li jej použít, můžete přidat následující prvek do souboru projektu Visual Basic ( \* . vbproj). Pokud je v systému nainstalovaná Visual Basic 15,5 nebo novější, umožní vám využít všechny jazykové funkce podporované nejnovější verzí Visual Basic kompilátoru:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Další informace najdete v tématu [nastavení jazykové verze Visual Basic](../configure-language-version.md).

> [!NOTE]
> V aplikaci Visual Studio, když vyberete nápovědu pro klávesu F1, získáte `private protected` nápovědu pro buď [soukromou](private.md) , nebo [chráněnou](protected.md). Rozhraní IDE vybere jeden token pod kurzorem namísto složeného slova.

## <a name="rules"></a>Pravidla

- **Kontext deklarace** Můžete použít `Private Protected` pouze na úrovni třídy. To znamená, že kontext deklarace pro `Protected` prvek musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.

## <a name="behavior"></a>Chování

- **Úroveň přístupu.** Veškerý kód ve třídě má přístup k jeho prvkům. Kód v jakékoli třídě, která je odvozena od základní třídy a je obsažen ve stejném sestavení, má přístup ke všem `Private Protected` prvkům základní třídy. Nicméně kód v jakékoli třídě, která je odvozena od základní třídy a je obsažen v jiném sestavení, nemůže přistupovat k `Private Protected` prvkům základní třídy.

- **Modifikátory přístupu.** Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*. Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

`Private Protected`V těchto kontextech lze použít modifikátor:

- [Příkaz třídy](../statements/class-statement.md) vnořené třídy

- [Const – příkaz](../statements/const-statement.md)

- [Declare – příkaz](../statements/declare-statement.md)

- [Příkaz Delegate](../statements/delegate-statement.md) pro delegáta vnořený ve třídě

- [Dim – příkaz](../statements/dim-statement.md)

- [Enum – příkaz](../statements/enum-statement.md) pro výčet vnořený ve třídě

- [Event – příkaz](../statements/event-statement.md)

- [Function – příkaz](../statements/function-statement.md)

- [Příkaz rozhraní](../statements/interface-statement.md) rozhraní vnořeného ve třídě

- [Property – příkaz](../statements/property-statement.md)

- [Příkaz struktury](../statements/structure-statement.md) struktury vnořené ve třídě

- [Sub – příkaz](../statements/sub-statement.md)

## <a name="see-also"></a>Viz také

- [Republik](public.md)
- [Proti](protected.md)
- [Friend](friend.md)
- [Hlášen](private.md)
- [Protected Friend](./protected-friend.md)
- [Úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
