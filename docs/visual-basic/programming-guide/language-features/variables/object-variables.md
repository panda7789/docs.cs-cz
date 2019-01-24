---
title: Proměnné objektu v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 046119664fc0277a6a5305d0cf086b4438b13f9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685461"
---
# <a name="object-variables-in-visual-basic"></a>Proměnné objektu v jazyce Visual Basic
Kromě ukládání hodnot přímo, mohou proměnné odkazovat na objekt. Přiřazení objektu k proměnné ze stejného důvodu, kterou přiřadíte libovolnou hodnotu proměnné:  
  
-   Název proměnné je často kratší a snadněji mějte na paměti než úplnou cestu k metodám a vlastnostem, které jsou potřebné pro přístup k objektu samotného.  
  
-   Použití proměnné, která odkazuje na objekt je efektivnější než opakovaně přístup k objektu samotného prostřednictvím nezbytné metody nebo vlastnosti.  
  
-   Můžete změnit proměnné k odkazování na jiné objekty, když váš kód běží.  
  
## <a name="making-code-shorter"></a>Provádění kódu kratší  
 Objektové proměnné můžete použít ke zkrácení kód, který je nutné zadat. Následující příklad používá pro přístup k úplnou cestu k metodám a vlastnostem <xref:System.Windows.Forms.Control> objektu.  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 Můžete zkrátit tento kód a rychlejší spuštění, pokud používáte proměnné objektu ovládacího prvku. By měla deklarovat proměnné objektu s konkrétní třídou, která máte v úmyslu přiřadit k ní (`Control` v tomto případě). Po přiřazení objektu k proměnné lze považovat ho stejně jako považovat objektu, na který odkazuje. Můžete nastavit nebo načíst vlastnosti objektu nebo použít některou z jeho metod. Následující příklad používá proměnné objektu pro zjednodušení kódu v předchozím příkladu.  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a>Viz také:
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Postupy: Urychlení přístupu k objektu pomocí cesty dlouhou kvalifikací](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
