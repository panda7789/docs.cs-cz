---
title: "Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed3201ef2bbef97eebbafa5ef128ca015adac013
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic).
Následující příklad kódu nastaví `Boolean` hodnotu, která určuje, zda řetězec reprezentuje platné datum nebo čas.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Nahraďte `("01/01/03")` a `"9:30 PM"` s datum a čas, kterou chcete ověřit. Je řetězec s jiným řetězcem pevně nahradit `String` proměnnou, nebo pomocí metody, vrátí řetězec, například `InputBox`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Použít tuto metodu ověření než se pokusíte převést řetězec `String` k `DateTime` proměnné. Nejdřív kontrolou datum nebo čas, se můžete vyhnout generování výjimku za běhu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [Ověřování řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
