---
title: 'Postupy: Deklarace objektové proměnné a přiřazení objektu k v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: e172d62e5bfadded254d5a5fd25b1dcf2da9634d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663579"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Postupy: Deklarace objektové proměnné a přiřazení objektu k v jazyce Visual Basic
Můžete deklarovat proměnnou [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) zadáním `As Object` v [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Přiřaďte objekt na takovou proměnnou tak, že objekt za znaménkem rovnítka (`=`) v klauzuli přiřazení příkazu nebo inicializace.  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `Object` proměnné a přiřazuje aktuální instance k němu.  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 Deklaraci a přiřazení můžete kombinovat pomocí inicializace proměnné jako součást její deklarace. Následující příklad je ekvivalentní k předchozímu příkladu.  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkaz na <xref:System> oboru názvů.  
  
- Třídy, struktury nebo modul, ve které chcete umístit `Dim` příkazu.  
  
- Postup, ve kterém chcete změnit příkazu přiřazení.  
  
## <a name="see-also"></a>Viz také:

- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
