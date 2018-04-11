---
title: Chybná konvence volání knihovny DLL
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a>Chybná konvence volání knihovny DLL
Argumenty předávané dynamická knihovna (DLL) musí přesně odpovídat názvům rutina očekává. Konvence volání řešit počet, typ a pořadí argumentů. Váš program může být volání rutiny v knihovně DLL, který je předáván nesprávného typu nebo počet argumentů.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zajistěte, aby že všechny typy argumentů souhlas s těmi, zadaný v deklaraci rutiny, která jsou volání.  
  
2.  Ujistěte se, že předáváte stejný počet argumentů uvedené v deklaraci rutiny, která jsou volání.  
  
3.  Pokud rutina DLL očekává argumentů podle hodnoty, ujistěte se, `ByVal` je zadán pro tyto argumenty v deklaraci pro rutiny.  
  
## <a name="see-also"></a>Viz také  
 [Typy chyb](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Call – příkaz](../../../visual-basic/language-reference/statements/call-statement.md)  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)
