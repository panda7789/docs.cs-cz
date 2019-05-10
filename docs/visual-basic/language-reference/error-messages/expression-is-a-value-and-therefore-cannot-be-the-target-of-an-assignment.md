---
title: Výraz je hodnota, a proto nemůže být cílem přiřazení.
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 1c7fb92c963ea7fa4129cddf060fe7c0b0261fc7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665146"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Výraz je hodnota, a proto nemůže být cílem přiřazení.
Příkaz se pokusí přiřadit hodnotu výrazu. Přiřadit hodnotu pouze pro zapisovatelné proměnná, vlastnost nebo prvku pole za běhu. Následující příklad ukazuje, jak k této chybě může dojít.  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 Podobné příklady může použít k vlastnostem a prvky pole.  
  
 **Nepřímý přístup.** Tuto chybu můžete vygenerovat také nepřímý přístup prostřednictvím hodnotového typu. Zvažte následující příklad kódu, která se pokusí nastavit hodnotu <xref:System.Drawing.Point> díky přístupu nepřímo prostřednictvím <xref:System.Windows.Forms.Control.Location%2A>.  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 Poslední příkaz v předchozím příkladu se nezdaří, protože se vytvoří dočasný přidělení pro <xref:System.Drawing.Point> vrácené struktury <xref:System.Windows.Forms.Control.Location%2A> vlastnost. Struktura je hodnotový typ a strukturu dočasné není zachována po spuštění příkazu. Problém je vyřešen deklarování a použití proměnné pro <xref:System.Windows.Forms.Control.Location%2A>, vytváří trvalejší přidělení pro <xref:System.Drawing.Point> struktury. Následující příklad ukazuje kód, který můžete nahradit poslední příkaz v předchozím příkladu.  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **ID chyby:** BC30068  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud příkaz přiřazuje hodnotu výrazu, nahraďte výraz jeden zapisovatelný proměnná, vlastnost nebo pole elementu.  
  
- Pokud příkaz vytváří nepřímý přístup prostřednictvím typu hodnoty (obvykle struktury), vytvořte proměnnou pro uchování hodnoty typu.  
  
- Přiřaďte proměnné vhodnou strukturou (nebo jiný typ hodnoty).  
  
- Pro přístup k vlastnosti k ní přiřadit hodnotu, použijte proměnnou.  
  
## <a name="see-also"></a>Viz také:

- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
- [Řešení potíží s procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
