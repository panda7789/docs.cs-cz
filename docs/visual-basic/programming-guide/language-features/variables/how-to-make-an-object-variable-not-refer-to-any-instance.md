---
title: 'Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci.'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: cce2e59cb76652937868a731ad308872d1aba2f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410448"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci (Visual Basic).
Můžete zrušit přidružení objektové proměnné z libovolné instance objektu nastavením na [hodnotu Nothing](../../../language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Zrušení přidružení objektové proměnné od libovolné instance objektu  
  
- Nastavte proměnnou na hodnotu `Nothing` v příkazu přiřazení.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud se váš kód pokusí o přístup ke členu proměnné objektu, která byla nastavena na `Nothing` , dojde k <xref:System.NullReferenceException> chybě. Pokud nastavíte proměnnou objektu na `Nothing` často, nebo pokud je možné, že proměnná není inicializována, je vhodné uzavřít přístup členů do `Try...Catch...Finally` bloku.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Použijete-li proměnnou objektu pro objekty, které obsahují důvěrná nebo citlivá data, můžete proměnnou nastavit na hodnotu, pokud aktivně nepracujete `Nothing` s jedním z těchto objektů. To snižuje riziko, že škodlivý kód získá přístup k datům.  
  
## <a name="see-also"></a>Viz také

- <xref:System.NullReferenceException>
- [Proměnné objektu](object-variables.md)
- [Přiřazení proměnné objektu](object-variable-assignment.md)
- [Nothing](../../../language-reference/nothing.md)
- [Try...Catch....Finally – příkaz](../../../language-reference/statements/try-catch-finally-statement.md)
