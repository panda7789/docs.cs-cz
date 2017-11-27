---
title: "& č. 39; IsNot & č. 39; operand typu & č. 39; typename & č. 39; lze porovnat pouze do & č. 39; Nic & č. 39; protože & č. 39; typename & č. 39; je typ s možnou hodnotou Null"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords: BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec0ae1561bfbee998e7c65f6023012c0f982a8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a>& č. 39; IsNot & č. 39; operand typu & č. 39; typename & č. 39; lze porovnat pouze do & č. 39; Nic & č. 39; protože & č. 39; typename & č. 39; je typ s možnou hodnotou Null
Proměnná definovaná jako s možnou hodnotou NULL byl porovnání s výrazem jiným než `Nothing` pomocí `IsNot` operátor.  
  
 **ID chyby:** BC32128  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  K porovnání typu s povolenou hodnotou Null pro výraz jiné než `Nothing` pomocí `IsNot` operátor, volání `GetType` metodu na typ s možnou hodnotou Null a porovnání výsledek výrazu, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a>Viz také  
 [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [IsNot – operátor](../../../visual-basic/language-reference/operators/isnot-operator.md)
