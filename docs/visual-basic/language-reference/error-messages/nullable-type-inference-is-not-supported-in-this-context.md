---
title: "V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords: BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e7a5450d812260d3916296dff56abee27b3d586c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
Typy hodnot a struktury lze deklarovat s možnou hodnotou Null.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 S možnou hodnotou Null deklarace však nelze použít v kombinaci s odvození typu. Následující příklady příčinou této chyby.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **ID chyby:** BC36629  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použijte `As` klauzule deklarovat proměnnou jako s možnou hodnotou Null.  
  
## <a name="see-also"></a>Viz také  
 [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
