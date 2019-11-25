---
title: Částečné
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: df85571b757fd54496677bad1195fab9690b79cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351361"
---
# <a name="partial-visual-basic"></a>Partial (Visual Basic)
Indicates that a type declaration is a partial definition of the type.  
  
 You can divide the definition of a type among several declarations by using the `Partial` keyword. You can use as many partial declarations as you want, in as many different source files as you want. However, all the declarations must be in the same assembly and the same namespace.  
  
> [!NOTE]
> Visual Basic supports *partial methods*, which are typically implemented in partial classes. For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attrlist`|Volitelné. List of attributes that apply to this type. You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).|  
|`accessmodifier`|Volitelné. Specifies what code can access this type. See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Volitelné. See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Volitelné. See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Požadováno. Name of this type. Must match the name defined in all other partial declarations of the same type.|  
|`Of`|Volitelné. Specifies that this is a generic type. See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md). See [Type List](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Volitelné. See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Required if you use `Inherits`. The name of the class or interface from which this class derives.|  
|`Implements`|Volitelné. See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Required if you use `Implements`. The names of the interfaces this type implements.|  
|`variabledeclarations`|Volitelné. Statements which declare additional variables and events for the type.|  
|`proceduredeclarations`|Volitelné. Statements which declare and define additional procedures for the type.|  
|`End Class` or `End Structure`|Ends this partial `Class` or `Structure` definition.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files. For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>. You should not modify the generated code in these controls.  
  
 All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.  
  
## <a name="best-practices"></a>Doporučené postupy  
  
- Under normal circumstances, you should not split the development of a single type across two or more declarations. Therefore, in most cases you do not need the `Partial` keyword.  
  
- For readability, every partial declaration of a type should include the `Partial` keyword. The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.  
  
## <a name="behavior"></a>Behavior  
  
- **Union of Declarations.** The compiler treats the type as the union of all its partial declarations. Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.  
  
- **Type Promotion Not Allowed For Partial Types in Modules.** If a partial definition is inside a module, type promotion of that type is automatically defeated. In such a case, a set of partial definitions can cause unexpected results and even compiler errors. For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     The compiler merges partial definitions only when their fully qualified paths are identical.  
  
 The `Partial` keyword can be used in these contexts:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Příklad  
 The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 The two partial definitions in the preceding example could be in the same source file or in two different source files.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
