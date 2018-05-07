---
title: 'Postupy: Volání přetížené procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 802a312d6ec6640594f3c6b662202d1ffcf2376d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Postupy: Volání přetížené procedury (Visual Basic)
Výhodou přetížení procedury je v flexibilitu volání. Volání kódu můžete získat informace, které je nutné předat postupu a pak zavolají název jedinou proceduru, bez ohledu na to, jaké argumentů je předávání.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>K volání procedury, která má definovaný více než jedna verze  
  
1.  Ve volání kódu určují, která data mají být předána do procesu.  
  
2.  Zápis volání procedury běžným způsobem, představuje data v seznamu argumentů. Ujistěte se, že argumenty, které odpovídají seznam parametrů v jednom z verzí definované pro proceduru.  
  
3.  Nemusíte určit, která verze postup volání. Visual Basic předá ovládacího prvku na verzi odpovídající vaší seznam argumentů.  
  
     Následující příklad volání `post` postup deklarované v [postupy: definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md). Ho získá Identifikace zákazníka, určuje, zda je `String` nebo `Integer`a potom v obou případech zavolá stejným způsobem.  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Řešení potíží s procedurami](./troubleshooting-procedures.md)  
 [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)  
 [Řešení přetížení](./overload-resolution.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
