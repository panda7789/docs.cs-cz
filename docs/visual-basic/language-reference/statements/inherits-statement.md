---
title: Inherits – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 6e6e9cc9210232059210862f2bda691c57b372d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353230"
---
# <a name="inherits-statement"></a>Inherits – příkaz
Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`basetypenames`|Požadováno. The name of the class from which this class derives.<br /><br /> -nebo-<br /><br /> The names of the interfaces from which this interface derives. Use commas to separate multiple names.|  
  
## <a name="remarks"></a>Poznámky  
 If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition. It should immediately follow the `Class` or `Interface` statement.  
  
 You can use `Inherits` only in a class or interface. This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.  
  
## <a name="rules"></a>Rules  
  
- **Class Inheritance.** If a class uses the `Inherits` statement, you can specify only one base class.  
  
     A class cannot inherit from a class nested within it.  
  
- **Interface Inheritance.** If an interface uses the `Inherits` statement, you can specify one or more base interfaces. You can inherit from two interfaces even if they each define a member with the same name. If you do so, the implementing code must use name qualification to specify which member it is implementing.  
  
     An interface cannot inherit from another interface with a more restrictive access level. For example, a `Public` interface cannot inherit from a `Friend` interface.  
  
     An interface cannot inherit from an interface nested within it.  
  
 An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class. This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.  
  
 An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface. This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.  
  
## <a name="example"></a>Příklad  
 The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Příklad  
 The following example shows inheritance of multiple interfaces.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`. A class that implements `thisInterface` must implement every member of every base interface.  
  
## <a name="see-also"></a>Viz také:

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
