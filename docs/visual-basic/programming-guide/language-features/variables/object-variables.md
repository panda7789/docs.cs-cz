---
title: Proměnné objektu v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 8383261c1806732c4c8abea9834000f003a848a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="object-variables-in-visual-basic"></a>Proměnné objektu v jazyce Visual Basic
Proměnné můžete kromě ukládání hodnot přímo, odkaz na objekt. Objekt můžete přiřadit proměnné ze stejného důvodu, který přiřadíte žádnou hodnotu proměnné:  
  
-   Název proměnné je často kratší a snadněji mějte na paměti, než úplnou cestu metod a vlastností, které jsou potřebné pro přístup k objektu sám sebe.  
  
-   Použití proměnné, která se vztahuje k objektu je efektivnější než opakovaně přístup k samotného objektu prostřednictvím nezbytné metody nebo vlastnosti.  
  
-   Můžete změnit proměnnou, která bude odkazovat na další objekty, když běží váš kód.  
  
## <a name="making-code-shorter"></a>Kratší provádění kódu  
 Objektové proměnné můžete použít tak, aby zkrátil kód, který je třeba zadávat. Následující příklad používá úplnou cestu metod a vlastností pro přístup <xref:System.Windows.Forms.Control> objektu.  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 Můžete zmenšit tento kód a urychlit spuštění, pokud používáte proměnné objektu pro ovládací prvek. Objektová proměnná s určité třídy, které chcete přiřadit k němu by měly deklarovat (`Control` v tomto případě). Po přiřazení objektu k proměnné, lze považovat ho stejně jako považovat objektu, na který odkazuje. Můžete nastavit nebo získat vlastnosti objektu nebo použít některou z jeho metod. Následující příklad používá proměnné objektu můžete zjednodušit kód v předchozím příkladu.  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a>Viz také  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
