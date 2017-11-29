---
title: "Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d91eeaeb034a4c8b4fefcffdf2fdebe72127d66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací (Visual Basic)
Pokud často přístup k objektu, který vyžaduje cestu kvalifikace několik metod a vlastností, můžete urychlit kódu není opakováním kvalifikace cestu.  
  
 Existují dva způsoby, kterými se můžete vyhnout. s opakováním kvalifikace cestu. Objekt můžete přiřadit k proměnné, nebo můžete použít v `With`... `End With` bloku.  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Pro urychlení přístupu k objektu výraznou kvalifikovaný přiřazením proměnné  
  
1.  Deklarace proměnné typu objektu, který často přistupují. Zadejte cestu kvalifikace v části inicializace deklaraci.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Použijte proměnnou pro přístup k objektu členy.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Pro urychlení přístupu k objektu výraznou kvalifikovaný pomocí With... End With bloku  
  
1.  Cesta kvalifikace chápat `With` příkaz.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Přístup ke členům objektu uvnitř `With` blokovat, než `End With` příkaz.  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [S... End With – příkaz](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
