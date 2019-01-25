---
title: Hodnoty proměnné objektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: ce38089e91b25cf50e738d956881f3a44bfa3306
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588720"
---
# <a name="object-variable-values-visual-basic"></a>Hodnoty proměnné objektu (Visual Basic)
Proměnná [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) mohou odkazovat na data libovolného typu. Hodnota ukládáte `Object` proměnná zůstane jinde v paměti, zatímco proměnné samotné drží ukazatel na data.  
  
## <a name="object-classifier-functions"></a>Objekt funkce třídění  
 Visual Basic poskytuje funkce, které vracejí informace o tom, co `Object` proměnná odkazuje na, jak je znázorněno v následující tabulce.  
  
|Funkce|Vrátí True, pokud je proměnná objektu odkazuje|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Pole hodnot, spíše než jednu hodnotu|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|A [Date – datový typ](../../../../visual-basic/language-reference/data-types/date-data-type.md) hodnotu nebo řetězec, který lze interpretovat jako hodnotu data a času|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Objekt typu <xref:System.DBNull>, která představuje data chybí nebo je nekonzistentní|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Objekt výjimky, která je odvozena z <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nic](../../../../visual-basic/language-reference/nothing.md), to znamená žádný objekt je aktuálně přiřazená k proměnné|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Číslo nebo řetězec, který může být interpretován jako číslo|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Typ odkazu (například řetězce, pole, delegáta nebo typ třídy)|  
  
 Tyto funkce můžete vyhnout odesílání neplatná hodnota pro operaci nebo proceduru.  
  
## <a name="typeof-operator"></a>TypeOf – operátor  
 Můžete také použít [TypeOf – operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md) k určení, zda proměnné objektu aktuálně odkazuje na konkrétní data typu. `TypeOf`... `Is` výraz vyhodnocen jako `True` run-time typu operandu je odvozený od nebo implementuje zadaného typu.  
  
 Následující příklad používá `TypeOf` v objektových proměnných odkazující na hodnotu a referenční typy.  
  
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
  
 Předchozí příklad zapíše následující řádky do **ladění** okno:  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 Objektová proměnná `num` odkazuje na datový typ `Integer`, a `frm` odkazuje na objekt třídy <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Pole objektů  
 Můžete deklarovat a používat celou řadu `Object` proměnné. To je užitečné, když potřebujete zpracovávat různé datové typy a třídy objektů. Všechny prvky pole musí mít stejné deklarovanému datovému typu. Tento datový typ jako deklarace `Object` umožňuje ukládat objekty a třídy instance společně s ostatními datovými typy v poli.  
  
## <a name="see-also"></a>Viz také:
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Postupy: Odkazování na aktuální instanci objektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Postupy: Určit, jaký typ proměnná objektu odkazuje](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Postupy: Určení, zda dva objekty souvisejí](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Postupy: Určení, zda dva objekty jsou identické](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
