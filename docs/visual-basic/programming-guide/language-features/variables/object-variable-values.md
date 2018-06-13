---
title: Hodnoty proměnné objektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: a5152ad0e5e5ac876783c2b191ee13e845593df8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652113"
---
# <a name="object-variable-values-visual-basic"></a>Hodnoty proměnné objektu (Visual Basic)
Proměnná [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md) mohou odkazovat na data libovolného typu. Hodnota uložená v `Object` proměnné je udržováno jinde v paměti, zatímco proměnnou obsahuje ukazatele na data.  
  
## <a name="object-classifier-functions"></a>Funkce třídění objektu  
 Visual Basic poskytuje funkce, které vracejí informace o tom, co `Object` proměnná odkazuje na, jak je znázorněno v následující tabulce.  
  
|Funkce|Vrátí hodnotu True, pokud je proměnná objektu odkazuje|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Pole hodnoty, než jednu hodnotu|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|A [Date – datový typ](../../../../visual-basic/language-reference/data-types/date-data-type.md) hodnota nebo řetězec, který lze interpretovat jako hodnota data a času|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Objekt typu <xref:System.DBNull>, která představuje data chybí, nebo neexistuje|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Objekt výjimky, která je odvozena z <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nic](../../../../visual-basic/language-reference/nothing.md), tedy žádný objekt je aktuálně přiřazen k proměnné|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Číslo nebo řetězec, který lze interpretovat jako číslo|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Odkaz na typ (například řetězce, pole, delegát nebo typu třídy)|  
  
 Aby se zabránilo odesílání neplatnou hodnotu pro operace nebo proceduru můžete použít tyto funkce.  
  
## <a name="typeof-operator"></a>TypeOf – operátor  
 Můžete také [typeof – operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md) k určení, zda proměnná objektu aktuálně odkazuje na konkrétní typ. `TypeOf`... `Is` výraz vyhodnocen jako `True` Pokud běhového typu operandu je odvozený od nebo implementuje zadaného typu.  
  
 Následující příklad používá `TypeOf` na objektové proměnné odkazující na typy hodnoty a odkazu.  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 V předchozím příkladu zapíše následující řádky, které se **ladění** okno:  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 Objektová proměnná `num` odkazuje na data typu `Integer`, a `frm` odkazuje na objekt třídy <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Pole objektů  
 Můžete deklarování a použití pole `Object` proměnné. To je užitečné, když potřebujete zpracovávat různé datové typy a tříd objektů. Všechny elementy ve pole musí mít stejný deklarované datový typ. Tento datový typ jako deklarace `Object` vám umožní ukládat objekty a třídy instance spolu s ostatními datovými typy v poli.  
  
## <a name="see-also"></a>Viz také  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Postupy: Odkazování na aktuální instanci objektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [Postupy: Určení, na jaký typ objektová proměnná odkazuje](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [Postupy: Určení, zda dva objekty spolu souvisí](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Postupy: Určení, zda dva objekty jsou identické](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
