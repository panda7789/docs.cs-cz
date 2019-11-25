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

Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.

## <a name="remarks"></a>Poznámky

The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members. The base class might undergo a change that creates an element with the same name as one you have already defined. If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.

Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches. For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).

## <a name="rules"></a>Rules

- **Declaration Context.** You can use `Shadows` only at class level. This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.

  You can declare only one shadowing element in a single declaration statement.

- **Combined Modifiers.** You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.

- **Element Types.** You can shadow any kind of declared element with any other kind. If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.

- **Accessing.** The shadowed element in the base class is normally unavailable from within the derived class that shadows it. However, the following considerations apply.

  - If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element. For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.

  - If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class. You can also access it through `MyBase`.

The `Shadows` modifier can be used in these contexts:

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
- [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
