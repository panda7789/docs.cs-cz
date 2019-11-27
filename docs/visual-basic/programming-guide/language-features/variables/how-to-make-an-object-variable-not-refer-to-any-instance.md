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
Můžete zrušit přidružení objektové proměnné z libovolné instance objektu nastavením na [hodnotu Nothing](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Zrušení přidružení objektové proměnné od libovolné instance objektu  
  
- Nastavte proměnnou na `Nothing` v příkazu přiřazení.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud se váš kód pokusí o přístup k členu proměnné objektu, která je nastavená na `Nothing`, dojde k <xref:System.NullReferenceException>. Pokud nastavíte proměnnou objektu na `Nothing` často, nebo pokud je možné, že proměnná není inicializována, je vhodné uzavřít přístup členů do bloku `Try...Catch...Finally`.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Použijete-li proměnnou objektu pro objekty, které obsahují důvěrná nebo citlivá data, můžete nastavit proměnnou na `Nothing`, pokud se neaktivně nepracujete s jedním z těchto objektů. To snižuje riziko, že škodlivý kód získá přístup k datům.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.NullReferenceException>
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Příkaz Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
