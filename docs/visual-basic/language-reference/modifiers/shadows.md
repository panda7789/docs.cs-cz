---
title: Shadows (Visual Basic)
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
ms.openlocfilehash: c9dfff99e2634b79ad6b44721f40583d21c9b98e
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664134"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

Určuje, že deklarovaný programový prvek znovu deklaruje a skryje identicky pojmenovanou elementu, nebo sadu přetížených elementů v základní třídě.

## <a name="remarks"></a>Poznámky

Hlavním účelem stínový provoz (což je také označován jako *skrývání podle názvu*) je zachovat definice členů třídy. Základní třídy může být změnu, která vytvoří element se stejným názvem jako ten, který je již definován. Pokud k tomu dojde, `Shadows` modifikátor vynutí odkazuje prostřednictvím vaší třídy, které je potřeba vyřešit členovi definované, namísto nový prvek základní třídy.

Jak stínováním a přepsáním znovu definovat element zděděné, ale existují významné rozdíly mezi dvěma přístupy. Další informace najdete v tématu [stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).

## <a name="rules"></a>pravidla

- **Místní deklarace.** Můžete použít `Shadows` pouze na úrovni třídy. To znamená, že deklarace kontext `Shadows` elementu musí být třída a nemůže být zdrojový soubor, obor názvů, rozhraní, modul, struktury nebo proceduru.

  Je možné deklarovat pouze jeden element stínového provozu v jedné deklaraci příkazu.

- **Kombinované modifikátory.** Nelze zadat `Shadows` spolu s `Overloads`, `Overrides`, nebo `Static` ve stejné deklaraci.

- **Typy elementů.** Můžete stínové jakýkoli druh element deklarovaný pomocí jakéhokoli druhu. Pokud jste stínovou kopii se vlastnost nebo procedura s jinou vlastnost nebo procedura, parametry a návratovým typem není potřeba odpovídají polím v základní třídě vlastnost nebo procedura.

- **Přístup k.** Stínovaný element v základní třídě je obvykle nedostupná z v rámci odvozené třídy, která zastiňuje ho. Nicméně platí následující aspekty.

  - Pokud stínového provozu element není přístupné z kódu na ni odkazuje, odkaz je přeložen na stínovaný elementu. Například pokud `Private` element zastiňuje prvek základní třídy, kód, který nemá oprávnění k přístupu `Private` element má přístup k elementu základní třídy místo toho.

  - Pokud jste stínové elementu, budete k němu přístup stínovaný element prostřednictvím objektu, který deklarovat s typem základní třídy. Můžete také k němu přístup prostřednictvím `MyBase`.

`Shadows` Modifikátor lze použít v těchto kontextech:

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
- [Stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
