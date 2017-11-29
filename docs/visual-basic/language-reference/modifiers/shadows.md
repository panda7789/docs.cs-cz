---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb767c372cc05d61d569227af8eef0dc3c67489b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const – příkaz](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Sdílené](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Statické](../../../visual-basic/language-reference/modifiers/static.md)  
 [Privátní](../../../visual-basic/language-reference/modifiers/private.md)  
 [ME, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Přetížení](../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Přepsání](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
