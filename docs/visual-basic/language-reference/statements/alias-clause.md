---
title: "Alias – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f61e738434ea616d751576ef21669545afc41397
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="alias-clause-visual-basic"></a>Alias – klauzule (Visual Basic)
Určuje, že externí procedura má jiný název v jeho knihovny DLL.  
  
## <a name="remarks"></a>Poznámky  
 `Alias` – Klíčové slovo lze použít v tomto kontextu:  
  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 V následujícím příkladu `Alias` – klíčové slovo slouží k zadání názvu funkce v advapi32.dll, `GetUserNameA`, že `getUserName` se v tomto příkladu používá místě. Funkce `getUserName` je volána v dílčí `getUser`, který zobrazí název aktuálního uživatele.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
