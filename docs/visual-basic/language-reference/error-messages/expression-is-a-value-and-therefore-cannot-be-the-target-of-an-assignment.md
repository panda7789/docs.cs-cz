---
title: "Výraz je hodnota, a proto nemůže být cílem přiřazení."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords: BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bec3e2d298160bd0b459dc3b7ef93b94648e439a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Výraz je hodnota, a proto nemůže být cílem přiřazení.
Příkaz se pokusí přiřadit hodnotu výrazu. V době běhu můžete přiřadit hodnotu pouze pro zápis proměnnou, vlastnost nebo pole elementu. Následující příklad ilustruje, jak této chybě může dojít.  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 Podobné příklady může použít k vlastnostem a prvků pole.  
  
 **Nepřímý přístup.** Nepřímý přístup prostřednictvím typ hodnoty můžete také vygenerovat tuto chybu. Vezměte v úvahu následující příklad kódu, který se pokouší nastavit hodnotu <xref:System.Drawing.Point> díky přístupu k nepřímo přes <xref:System.Windows.Forms.Control.Location%2A>.  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 Poslední příkaz v předchozím příkladu selže, protože se tím vytvoří dočasný přidělení pro <xref:System.Drawing.Point> struktura vrácený <xref:System.Windows.Forms.Control.Location%2A> vlastnost. Struktura je typ hodnoty a strukturu dočasné nezůstanou zachovány po spuštění příkazu. Deklarování a použití proměnné pro vyřešení problému <xref:System.Windows.Forms.Control.Location%2A>, která vytvoří více trvalých přidělení pro <xref:System.Drawing.Point> struktura. Následující příklad ukazuje kód, který můžete nahradit poslední příkaz v předchozím příkladu.  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **ID chyby:** BC30068  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud příkaz přiřazuje hodnotu výrazu, nahraďte výraz jedné proměnné s možností zápisu, vlastnost nebo pole elementu.  
  
-   Pokud se příkaz provede nepřímý přístup prostřednictvím typu hodnoty (obvykle struktura), vytvořte proměnnou pro uložení typ hodnoty.  
  
-   Přiřaďte proměnnou strukturu odpovídající (nebo jiný typ hodnota).  
  
-   Použijte proměnnou pro přístup k vlastnosti ji přiřadit hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Řešení potíží s procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
