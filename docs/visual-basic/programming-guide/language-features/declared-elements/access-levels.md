---
title: Úrovně přístupu
ms.date: 05/10/2018
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private Protected access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: 33a218a2acc3c876428d6c9a887280a559f84323
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348683"
---
# <a name="access-levels-in-visual-basic"></a>Úrovně přístupu v jazyce Visual Basic

The *access level* of a declared element is the extent of the ability to access it, that is, what code has permission to read it or write to it. This is determined not only by how you declare the element itself, but also by the access level of the element's container. Code that cannot access a containing element cannot access any of its contained elements, even those declared as `Public`. For example, a `Public` variable in a `Private` structure can be accessed from inside the class that contains the structure, but not from outside that class.

## <a name="public"></a>Public

The [Public](../../../language-reference/modifiers/public.md) keyword in the declaration statement specifies that the element can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project. The following code shows a sample `Public` declaration:

```vb
Public Class ClassForEverybody
```

You can use `Public` only at module, interface, or namespace level. This means you can declare a public element at the level of a source file or namespace, or inside an interface, module, class, or structure, but not in a procedure.
  
## <a name="protected"></a>Chráněno

The [Protected](../../../language-reference/modifiers/protected.md) keyword in the declaration statement specifies that the element can be accessed only from within the same class, or from a class derived from this class. The following code shows a sample `Protected` declaration:

```vb
Protected Class ClassForMyHeirs
```

You can use `Protected` only at class level, and only when you declare a member of a class. This means you can declare a protected element in a class, but not at the level of a source file or namespace, or inside an interface, module, structure, or procedure.

## <a name="friend"></a>Friend

The [Friend](../../../language-reference/modifiers/friend.md) keyword in the declaration statement specifies that the element can be accessed from within the same assembly, but not from outside the assembly. The following code shows a sample `Friend` declaration:

```vb
Friend stringForThisProject As String
```

You can use `Friend` only at module, interface, or namespace level. This means you can declare a friend element at the level of a source file or namespace, or inside an interface, module, class, or structure, but not in a procedure.

## <a name="protected-friend"></a>Protected Friend

The [Protected Friend](../../../language-reference/modifiers/protected-friend.md) keyword combination in the declaration statement specifies that the element can be accessed either from derived classes or from within the same assembly, or both. The following code shows a sample `Protected Friend` declaration:

```vb
Protected Friend stringForProjectAndHeirs As String
```

You can use `Protected Friend` only at class level, and only when you declare a member of a class. This means you can declare a protected friend element in a class, but not at the level of a source file or namespace, or inside an interface, module, structure, or procedure.

## <a name="private"></a>Soukromé

The [Private](../../../language-reference/modifiers/private.md) keyword in the declaration statement specifies that the element can be accessed only from within the same module, class, or structure. The following code shows a sample `Private` declaration:

```vb
Private _numberForMeOnly As Integer
```

You can use `Private` only at module level. This means you can declare a private element inside a module, class, or structure, but not at the level of a source file or namespace, inside an interface, or in a procedure.

At the module level, the `Dim` statement without any access level keywords is equivalent to a `Private` declaration. However, you might want to use the `Private` keyword to make your code easier to read and interpret.

## <a name="private-protected"></a>Private Protected

The [Private Protected](../../../language-reference/modifiers/private-protected.md) keyword combination in the declaration statement specifies that the element can be accessed only from within the same class, as well as from derived classes found in the same assembly as the containing class. The `Private Protected` access modifier is supported starting with Visual Basic 15.5.

The following example shows a `Private Protected` declaration:

```vb
Private Protected internalValue As Integer
```

You can declare a `Private Protected` element only inside of a class. You cannot declare it within an interface or structure, nor can you declare it at the level of a source file or namespace, inside an interface or a structure, or in a procedure.

The `Private Protected` access modifier is supported by Visual Basic 15.5 and later. To use it, you add the following element to your Visual Basic project ( *\*.vbproj*) file. As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

To use the `Private Protected` access modifier, you must add the following element to your Visual Basic project ( *\*.vbproj*) file:

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).

## <a name="access-modifiers"></a>Modifikátory přístupu

The keywords that specify access level are called *access modifiers*. The following table compares the access modifiers:

|Access modifier|Access level granted|Elements you can declare with this access level|Declaration context within which you can use this modifier|
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|
|`Public`|Unrestricted:<br /><br /> Any code that can see a public element can access it|Rozhraní<br /><br /> Moduly<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Structure members<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Member variables<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> External declarations<br /><br /> Delegáty|Source file<br /><br /> Obor názvů<br /><br /> Rozhraní<br /><br /> Modul<br /><br /> Třída<br /><br /> Struktura|
|`Protected`|Derivational:<br /><br /> Code in the class that declares a protected element, or a class derived from it, can access the element|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Member variables<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> External declarations<br /><br /> Delegáty|Třída|
|`Friend`|Sestavení:<br /><br /> Code in the assembly that declares a friend element can access it|Rozhraní<br /><br /> Moduly<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Structure members<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Member variables<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> External declarations<br /><br /> Delegáty|Source file<br /><br /> Obor názvů<br /><br /> Rozhraní<br /><br /> Modul<br /><br /> Třída<br /><br /> Struktura|
|`Protected``Friend`|Union of `Protected` and `Friend`:<br /><br /> Code in the same class or the same assembly as a protected friend element, or within any class derived from the element's class, can access it|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Member variables<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> External declarations<br /><br /> Delegáty|Třída|
|`Private`|Declaration context:<br /><br /> Code in the type that declares a private element, including code within contained types, can access the element|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Structure members<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Member variables<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> External declarations<br /><br /> Delegáty|Modul<br /><br /> Třída<br /><br /> Struktura|
|`Private Protected`|Code in the class that declares a private protected element, or code in a derived class found in the same assembly as the bas class.|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Member variables<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> External declarations<br /><br /> Delegáty|Třída|

## <a name="see-also"></a>Viz také:

- [Příkaz Dim](../../../language-reference/statements/dim-statement.md)
- [Static](../../../language-reference/modifiers/static.md)
- [Deklarované názvy elementů](declared-element-names.md)
- [Odkazy na deklarované elementy](references-to-declared-elements.md)
- [Deklarované charakteristiky elementů](declared-element-characteristics.md)
- [Lifetime in Visual Basic](lifetime.md)
- [Scope in Visual Basic](scope.md)
- [Postupy: Řízení dostupnosti proměnné](how-to-control-the-availability-of-a-variable.md)
- [Proměnné](../variables/index.md)
- [Deklarace proměnné](../variables/variable-declaration.md)
