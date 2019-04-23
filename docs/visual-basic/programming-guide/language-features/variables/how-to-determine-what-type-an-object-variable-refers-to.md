---
title: 'Postupy: Určit, jaký typ proměnná objektu odkazuje (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 6499dfce880cc9ce16e5d77887afc0598692f48e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342866"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Postupy: Určit, jaký typ proměnná objektu odkazuje (Visual Basic)
Objektová proměnná obsahuje ukazatel na data, která je uložená na jiném místě. Typ těchto dat můžete změnit za běhu. V daném okamžiku provádějí, můžete použít <xref:System.Type.GetTypeCode%2A> metodou ke zjištění aktuálního typu za běhu nebo [TypeOf – operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md) zjistit, jestli aktuální run-time typu je kompatibilní s zadaného typu.  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Chcete-li zjistit, konkrétní typ proměnná objektu aktuálně odkazuje na  
  
1. Proměnné objektu volat <xref:System.Object.GetType%2A> metodu pro načtení <xref:System.Type?displayProperty=nameWithType> objektu.  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2. Na <xref:System.Type?displayProperty=nameWithType> třídy, zavolejte metodu sdílené <xref:System.Type.GetTypeCode%2A> načíst <xref:System.TypeCode> hodnotu výčtu pro typ objektu.  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Můžete testovat <xref:System.TypeCode> hodnoty výčtu s libovolným členy výčtu jsou zajímavé, jako je například `Double`.  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>K určení, zda objekt je kompatibilní s typem zadaný typ proměnné  
  
-   Použití `TypeOf` operátor v kombinaci s [je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) otestovat objekt s `TypeOf`... `Is` výrazu.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     `TypeOf`... `Is` výraz vrátí `True` Pokud objektu za běhu typ je kompatibilní se zadaným typem.  
  
     Kritéria pro kompatibilitu závisí na tom, zda zadaný typ třídy, struktury nebo rozhraní. Obecně platí jsou kompatibilní typy, pokud objekt je stejného typu jako, dědí z nebo implementuje zadaného typu. Další informace najdete v tématu [TypeOf operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Všimněte si, že zadaný typ nemůže být proměnné nebo výrazu. Musí být název definovaný typ, jako jsou třídy, struktury nebo rozhraní. To zahrnuje vnitřní typy jako `Integer` a `String`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
