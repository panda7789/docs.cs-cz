---
title: "Call – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a>Call – příkaz (Visual Basic)
Přenos řízení `Function`, `Sub`, nebo postup dynamická knihovna (DLL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Součásti  
 `procedureName`  
 Požadováno. Název procedury k volání.  
  
 `argumentList`  
 Volitelné. Seznam proměnných nebo výrazů představující argumenty, které se budou předávat procesu při jejím volání. Více argumentů jsou oddělené čárkami. Pokud zahrnete `argumentList`, je nutné uzavřít do závorek.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Call` – klíčové slovo při volání procedury. Pro většinu volání procedur není nutné používat toto klíčové slovo.  
  
 Obvykle se používá `Call` – klíčové slovo volané výraz nezačíná identifikátor. Použití `Call` – klíčové slovo pro jiné účely se nedoporučuje.  
  
 Pokud postup vrátí hodnotu, `Call` příkaz zruší ho.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje dva příklady kde `Call` – klíčové slovo je potřeba volání procedury. V obou příkladech volané výraz nezačíná identifikátor.  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Lambda – výrazy](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
