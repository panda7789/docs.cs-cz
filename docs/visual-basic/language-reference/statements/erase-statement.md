---
title: "Erase – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a>Erase – příkaz (Visual Basic)
Použít k vydání proměnné pole a navrátit paměť použitá pro jejich elementů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>Součásti  
 `arraylist`  
 Požadováno. Seznam proměnné pole, které chcete vymazat. Více proměnných jsou oddělené čárkami.  
  
## <a name="remarks"></a>Poznámky  
 `Erase` Příkaz může vyskytovat pouze na úrovni postupu. To znamená, že můžete vydat pole uvnitř procedury, ale ne na úrovni třídy nebo modulu.  
  
 `Erase` Příkaz je ekvivalentní k přiřazení `Nothing` pro každou proměnnou pole.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Erase` příkaz dvě pole vymazat a uvolnit paměť, jejich (elementy úložiště 1000 a 100, v uvedeném pořadí). `ReDim` Příkaz poté přiřadí novou instanci pole k poli trojrozměrné.  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Nic](../../../visual-basic/language-reference/nothing.md)  
 [ReDim – příkaz](../../../visual-basic/language-reference/statements/redim-statement.md)
