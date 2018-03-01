---
title: "Příkaz není platný uvnitř metoda-víceřádkového výrazu lambda"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80673fc7a1497b4148a6505d29581c6403115558
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a>Příkaz není platný uvnitř metody nebo víceřádkového výrazu lambda.
Příkaz není platný v rámci `Sub`, `Function`, vlastnost `Get`, nebo vlastnost `Set` postupu. Některé příkazy mohou být umístěny na úrovni modulu nebo třídy. Jiné, jako například `Option Strict`, musí být na úrovni oboru názvů a předcházet všechny ostatní deklarace.  
  
 **ID chyby:** BC30024  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte příkaz v postupu.  
  
## <a name="see-also"></a>Viz také  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Get – příkaz](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set – příkaz](../../../visual-basic/language-reference/statements/set-statement.md)
