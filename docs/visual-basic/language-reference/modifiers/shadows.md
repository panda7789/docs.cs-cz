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
ms.openlocfilehash: e9a423fa69ad1dcd8c1d4a5b7085e5b5da548f93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351265"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

Určuje, že deklarovaný programový prvek znovu deklaruje a skryje identicky pojmenovaný element nebo množinu přetížených prvků v základní třídě.

## <a name="remarks"></a>Poznámky

Hlavní účel vytváření stínových kopií (který se také označuje jako *skrytí podle názvu*) je zachování definice členů vaší třídy. Základní třída se může podrobit změně, která vytvoří element se stejným názvem jako ten, který jste už definovali. Pokud k tomu dojde, modifikátor `Shadows` vynutí, aby byly odkazy prostřednictvím vaší třídy přeloženy na člen, který jste definovali, místo na nový prvek základní třídy.

Jak Stínová, tak i přepsání předefinují zděděný element, ale existují významné rozdíly mezi těmito dvěma přístupy. Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).

## <a name="rules"></a>Pravidla

- **Kontext deklarace** `Shadows` lze použít pouze na úrovni třídy. To znamená, že kontext deklarace pro prvek `Shadows` musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.

  V jednom příkazu deklarace lze deklarovat pouze jeden element shadowing.

- **Kombinované modifikátory.** V rámci stejné deklarace nelze zadat `Shadows` společně s `Overloads`, `Overrides`nebo `Static`.

- **Typy prvků.** Můžete vystínovat jakýkoliv druh deklarovaného prvku s jakýmkoli jiným druhem. Pokud nastínete vlastnost nebo proceduru pomocí jiné vlastnosti nebo procedury, parametry a návratový typ nemusejí odpovídat hodnotám ve vlastnosti nebo proceduře základní třídy.

- **Přístup k.** Stínovaný element v základní třídě není obvykle k dispozici v odvozené třídě, která ho nastínuje. Platí však následující požadavky.

  - Pokud není stínový element přístupný z kódu, který se na něj odkazuje, odkaz je přeložen na stínovaný element. Například pokud `Private` element stínování elementu základní třídy, kód, který nemá oprávnění pro přístup k `Private` elementu, přistupuje k elementu základní třídy místo toho.

  - Pokud vytvoříte stín elementu, můžete ke stínovaný element přistupovat i přes objekt deklarovaný s typem základní třídy. K němu taky můžete přistupovat prostřednictvím `MyBase`.

V těchto kontextech lze použít modifikátor `Shadows`:

- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)

- [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)

- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)

- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)

- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)

- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)

- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Viz také:

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Me, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Stínování v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
