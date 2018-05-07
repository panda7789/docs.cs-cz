---
title: 'Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 1f38c90f0571b3fc73c4c89812092cdada936d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic
Deklarace proměnné [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md) zadáním `As Object` v [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md). Přiřazení objektu k tuto proměnnou tím, že objekt za znaménkem rovnítka (`=`) v klauzuli příkaz nebo inicializace přiřazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `Object` proměnnou a přiřadí aktuální instance k němu.  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 Deklarace a přiřazení můžete kombinovat podle inicializace proměnné jako součást jeho deklaraci. Následující příklad je ekvivalentní v předcházejícím příkladu.  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na <xref:System> oboru názvů.  
  
-   Třída, struktura nebo modul, ve kterém se umístí `Dim` příkaz.  
  
-   Postup, do kterého chcete vložit příkaz přiřazení.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
