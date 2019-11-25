---
title: Nedostatek místa v zásobníku
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349186"
---
# <a name="out-of-stack-space-visual-basic"></a>Nedostatek místa v zásobníku (Visual Basic)
The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program. Its limits have been exceeded.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Check that procedures are not nested too deeply.  
  
2. Make sure recursive procedures terminate properly.  
  
3. If local variables require more local variable space than is available, try declaring some variables at the module level. You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`. Or you can use the `Static` statement to declare individual static variables within procedures.  
  
4. Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings. You can also define the string at module level where it requires no stack space.  
  
5. Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.  
  
6. Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack. An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code. Use the `Calls` dialog box to view which procedures are active on the stack.  
  
## <a name="see-also"></a>Viz také:

- [Okna paměti](/visualstudio/debugger/memory-windows)
