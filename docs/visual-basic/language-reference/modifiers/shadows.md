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
ms.openlocfilehash: 4ca4ec48ee63b71447056a2c5cb68e8948f27ad0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)
Určuje, že deklarované programovací element redeclares a skryje stejně jako s názvem prvku, nebo sadu přetížené elementů v základní třídě.  
  
## <a name="remarks"></a>Poznámky  
 Hlavním účelem stínový provoz (což je také označován jako *skrytí podle názvu*) se zachovat definici členy vaší třídy. Základní třída může podstoupit změnu, která vytvoří element se stejným názvem jako jeden, který je již definován. V takovém případě `Shadows` modifikátor vynutí odkazuje prostřednictvím vaší třídy přeloží na člen definované, místo do nového elementu základní třídy.  
  
 Jak stínováním a přepsáním znovu definovat zděděné elementu, ale existují významné rozdíly mezi dva přístupy. Další informace najdete v tématu [stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="rules"></a>Pravidla  
  
-   **Kontext deklarace.** Můžete použít `Shadows` jenom na úrovni třídy. To znamená kontext deklarace `Shadows` element musí být třída a nesmí být zdrojový soubor, obor názvů, rozhraní, modul, struktura nebo postup.  
  
     Lze deklarovat pouze jeden element stínového provozu v jediné deklaraci příkazu.  
  
-   **Kombinovaná parametrů.** Nelze zadat `Shadows` společně s `Overloads`, `Overrides`, nebo `Static` ve stejné deklaraci.  
  
-   **Typy elementů.** Můžete stínové jakýkoli druh deklarovaný element s jakéhokoli jiného typu. Pokud jste stínové vlastnosti nebo procedury s jinou vlastnost nebo postup, parametry a návratový typ nemusí se shodovat s hodnotami ve vlastnosti základní třídu nebo postupu.  
  
-   **Přístup k.** Element stíněné v základní třídě je obvykle ze není k dispozici v rámci odvozené třídy, stín ho. Nicméně, platí následující aspekty.  
  
    -   Pokud element stínového provozu není přístupný z kódu na ně odkazovat, odkaz je přeložen na stíněné elementu. Například pokud `Private` element shadows prvku základní třídy, kód, který nemá oprávnění k přístupu `Private` element přistupuje k prvku základní třídy místo.  
  
    -   Pokud jste stínové element, můžete ke stíněné element prostřednictvím objektu deklarovat s typem základní třídy. Můžete taky přejít přes `MyBase`.  
  
 `Shadows` Modifikátor lze použít v těchto kontexty:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Static](../../../visual-basic/language-reference/modifiers/static.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Me, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
