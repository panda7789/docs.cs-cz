---
title: Shadows
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: 7aed6bec21bd484cca019b061bd5915de13a9eb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402704"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

Určuje, že deklarovaný programový prvek znovu deklaruje a skryje identicky pojmenovaný element nebo množinu přetížených prvků v základní třídě.

## <a name="remarks"></a>Poznámky

Hlavní účel vytváření stínových kopií (který se také označuje jako *skrytí podle názvu*) je zachování definice členů vaší třídy. Základní třída se může podrobit změně, která vytvoří element se stejným názvem jako ten, který jste už definovali. Pokud k tomu dojde, `Shadows` Modifikátor vynutí, aby byly odkazy prostřednictvím vaší třídy přeloženy na člen, který jste definovali, místo na nový prvek základní třídy.

Jak Stínová, tak i přepsání předefinují zděděný element, ale existují významné rozdíly mezi těmito dvěma přístupy. Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).

## <a name="rules"></a>Pravidla

- **Kontext deklarace** Můžete použít `Shadows` pouze na úrovni třídy. To znamená, že kontext deklarace pro `Shadows` prvek musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.

  V jednom příkazu deklarace lze deklarovat pouze jeden element shadowing.

- **Kombinované modifikátory.** Nelze zadat `Shadows` společně s `Overloads` , `Overrides` nebo `Static` ve stejné deklaraci.

- **Typy prvků.** Můžete vystínovat jakýkoliv druh deklarovaného prvku s jakýmkoli jiným druhem. Pokud nastínete vlastnost nebo proceduru pomocí jiné vlastnosti nebo procedury, parametry a návratový typ nemusejí odpovídat hodnotám ve vlastnosti nebo proceduře základní třídy.

- **Přístup k.** Stínovaný element v základní třídě není obvykle k dispozici v odvozené třídě, která ho nastínuje. Platí však následující požadavky.

  - Pokud není stínový element přístupný z kódu, který se na něj odkazuje, odkaz je přeložen na stínovaný element. Například pokud `Private` prvek vystínuje element základní třídy, kód, který nemá oprávnění pro přístup k `Private` elementu, přistupuje k elementu základní třídy.

  - Pokud vytvoříte stín elementu, můžete ke stínovaný element přistupovat i přes objekt deklarovaný s typem základní třídy. K němu máte přístup i přes `MyBase` .

`Shadows`V těchto kontextech lze použít modifikátor:

- [Class – příkaz](../statements/class-statement.md)

- [Const – příkaz](../statements/const-statement.md)

- [Declare – příkaz](../statements/declare-statement.md)

- [Delegate – příkaz](../statements/delegate-statement.md)

- [Dim – příkaz](../statements/dim-statement.md)

- [Enum – příkaz](../statements/enum-statement.md)

- [Event – příkaz](../statements/event-statement.md)

- [Function – příkaz](../statements/function-statement.md)

- [Interface – příkaz](../statements/interface-statement.md)

- [Property – příkaz](../statements/property-statement.md)

- [Structure – příkaz](../statements/structure-statement.md)

- [Sub – příkaz](../statements/sub-statement.md)

## <a name="see-also"></a>Viz také

- [Shared](shared.md)
- [Tras](static.md)
- [Hlášen](private.md)
- [Me, My, MyBase a MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Přetížení](overloads.md)
- [Overridable](overridable.md)
- [Přepsání](overrides.md)
- [Stínění v jazyce Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
