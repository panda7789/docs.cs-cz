---
title: 'Postupy: Urychlení přístupu k objektu pomocí cesty dlouhou kvalifikací (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 94c838a69aab9fcae9dc0c79b6038ee90e2369e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769041"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Postupy: Urychlení přístupu k objektu pomocí cesty dlouhou kvalifikací (Visual Basic)
Pokud využíváte častěji objekt, který se vyžaduje cesta kvalifikace několik metod a vlastností, můžete urychlit kódu není opakováním cesta kvalifikace.  
  
 Existují dva způsoby opakující se cesta kvalifikace se můžete vyhnout. Objekt můžete přiřadit k proměnné nebo ho můžete použít `With`... `End With` bloku.  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Ke zrychlení přístupu k objektu silně kvalifikovaný přiřazením do proměnné  
  
1. Deklarujte proměnnou typu objektu, který často přistupujete. Zadejte cestu kvalifikace v inicializaci části prohlášení.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2. Pro přístup ke členům objektu, použijte proměnnou.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>K urychlení přístupu k objektu silně kvalifikovaný pomocí With... Blok End With  
  
1. Vložit cestu kvalifikaci `With` příkazu.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2. Přístup ke členům objektu uvnitř `With` blokovat, než `End With` příkazu.  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Příkaz With...End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
