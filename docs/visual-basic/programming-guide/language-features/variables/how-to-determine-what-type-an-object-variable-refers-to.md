---
title: "Postupy: Určení, na jaký typ proměnná objektu odkazuje (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5dd6785ecd48be3f0455de63b9e3f13a485ddbb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Postupy: Určení, na jaký typ proměnná objektu odkazuje (Visual Basic)
Proměnné objektu obsahuje ukazatel na data, která je uložená na jiném místě. Typ dat, můžete změnit za běhu. V každém okamžiku můžete použít <xref:System.Type.GetTypeCode%2A> metoda k určení aktuální typ spuštění nebo [typeof – operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md) zjistit, jestli aktuální běhového typu je kompatibilní s zadaného typu.  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Chcete-li zjistit, že že přesný typ proměnná objektu aktuálně odkazuje na  
  
1.  Na proměnnou objekt volání <xref:System.Object.GetType%2A> metoda pro načtení <xref:System.Type?displayProperty=nameWithType> objektu.  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  Na <xref:System.Type?displayProperty=nameWithType> třídy, volejte metodu sdílené <xref:System.Type.GetTypeCode%2A> načíst <xref:System.TypeCode> hodnota výčtu pro typ objektu.  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Můžete otestovat <xref:System.TypeCode> hodnoty výčtu s kteroukoli členy výčtu jsou zájmu, například `Double`.  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>K určení, zda objekt je kompatibilní s typem zadaný typ proměnné  
  
-   Použití `TypeOf` operátor v kombinaci s [je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) k testování objekt s `TypeOf`... `Is` výraz.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     `TypeOf`... `Is` výraz vrátí `True` Pokud objekt je spuštění typ je kompatibilní se zadaným typem.  
  
     Kritéria pro kompatibilitu závisí na tom, zda zadaný typ je třída, struktura nebo rozhraní. Typy jsou obecně kompatibilní Pokud objekt je stejného typu jako, dědí z nebo implementuje zadaného typu. Další informace najdete v tématu [typeof – operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Všimněte si, že zadaný typ nemůže být proměnné nebo výrazu. Musí být název určitého typu, například třída, struktura nebo rozhraní. Jedná se o vnitřní typy, jako `Integer` a `String`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.GetTypeCode%2A>  
 <xref:System.TypeCode>  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Hodnoty proměnné objektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md)
