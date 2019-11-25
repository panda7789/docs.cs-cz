---
title: 'Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci.'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 320dadb61c12f3339c5328dcef31c41503892c56
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352885"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci (Visual Basic).
You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>To disassociate an object variable from any object instance  
  
- Set the variable to `Nothing` in an assignment statement.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Robustní programování  
 If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs. If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects. This reduces the chance of malicious code gaining access to the data.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.NullReferenceException>
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Příkaz Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
