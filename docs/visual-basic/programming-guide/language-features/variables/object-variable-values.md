---
title: Hodnoty proměnné objektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 728f097b3c084e5292cb2d2bf5a0c1d20bdad922
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004581"
---
# <a name="object-variable-values-visual-basic"></a>Hodnoty proměnné objektu (Visual Basic)
Proměnná [datového typu objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) může odkazovat na data libovolného typu. Hodnota, kterou uložíte v proměnné `Object`, je ponechána jinde v paměti, zatímco proměnná sama obsahuje ukazatel na data.  
  
## <a name="object-classifier-functions"></a>Funkce třídění objektů  
 Visual Basic poskytuje funkce, které vracejí informace o tom, co proměnná `Object` odkazuje na, jak je znázorněno v následující tabulce.  
  
|Funkce|Vrátí hodnotu true, pokud proměnná objektu odkazuje na|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Pole hodnot, nikoli jediná hodnota|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|Hodnota [datového typu](../../../../visual-basic/language-reference/data-types/date-data-type.md) data nebo řetězec, který může být interpretován jako hodnota data a času.|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Objekt typu <xref:System.DBNull>, který představuje chybějící nebo neexistující data|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Objekt výjimky, který je odvozen z <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nothing](../../../../visual-basic/language-reference/nothing.md), to znamená, že žádný objekt není aktuálně přiřazen k proměnné|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Číslo nebo řetězec, který může být interpretován jako číslo|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Typ odkazu (například řetězec, pole, delegát nebo typ třídy)|  
  
 Tyto funkce můžete použít, chcete-li se vyhnout odeslání neplatné hodnoty do operace nebo procedury.  
  
## <a name="typeof-operator"></a>TypeOf – operátor  
 Můžete také použít [operátor typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) k určení, zda objektová proměnná aktuálně odkazuje na konkrétní datový typ. Výraz `TypeOf`... `Is` je vyhodnocen jako `True`, pokud je typ běhu operand odvozen z nebo implementuje zadaný typ.  
  
 Následující příklad používá `TypeOf` u proměnných objektu odkazujících na typy hodnot a odkazů.  
  
```vb  
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
  
 Předchozí příklad zapíše následující řádky do okna **ladění** :  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 Proměnná objektu `num` odkazuje na data typu `Integer` a `frm` odkazuje na objekt třídy <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Pole objektů  
 Můžete deklarovat a použít pole proměnných `Object`. To je užitečné v případě, že potřebujete zpracovat nejrůznější datové typy a třídy objektů. Všechny elementy v poli musí mít stejný deklarovaný datový typ. Deklarování tohoto datového typu jako `Object` umožňuje ukládat objekty a instance třídy společně s jinými datovými typy v poli.  
  
## <a name="see-also"></a>Viz také:

- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Postupy: Odkazování na aktuální instanci objektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Postupy: Určení, na jaký typ objektová proměnná odkazuje](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Postupy: Určení, zda dva objekty spolu souvisí](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Postupy: Určení, zda dva objekty jsou identické](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
