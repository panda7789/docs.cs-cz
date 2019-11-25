---
title: Kdy použít výčet
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 5daae8d487ddfe079a54e305e59e32e8ded8f65e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353961"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Kdy použít výčet (Visual Basic)
Enumerations offer an easy way to work with sets of related constants. An enumeration, or `Enum`, is a symbolic name for a set of values. Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.  
  
## <a name="when-to-use-an-enumeration"></a>Kdy použít výčet  
 Whenever a procedure accepts a limited set of variables, consider using an enumeration. Enumerations make for clearer and more readable code, particularly when meaningful names are used.  
  
 The benefits of using enumerations include:  
  
- Reduces errors caused by transposing or mistyping numbers.  
  
- Makes it easy to change values in the future.  
  
- Makes code easier to read, which means it is less likely that errors will creep into it.  
  
- Ensures forward compatibility. With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.  
  
## <a name="naming-enumerations"></a>Naming Enumerations  
 Use a naming convention for enumeration members. When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name. Use a unique prefix that identifies the values from your application or component.  
  
 When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement. For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Predefined Enumerations  
 Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code. For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Viz také:

- [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
