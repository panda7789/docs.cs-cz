---
title: "Stop – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b7f04214234837a86bf0c77c0d7b6934e2babd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="stop-statement-visual-basic"></a>Stop – příkaz (Visual Basic)
Pozastaví spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete umístit `Stop` příkazy kdekoli v postupech pozastavit provádění. Pomocí `Stop` příkaz je podobná nastavením zarážky v kódu.  
  
 `Stop` Příkaz pozastaví spuštění, ale na rozdíl od `End`, nemá zavřete všechny soubory, nebo zrušte všechny proměnné, pokud se vyskytuje v kompilovaném spustitelný soubor (.exe) soubor.  
  
> [!NOTE]
>  Pokud `Stop` je příkaz zjistil v kódu, který je spuštěn mimo integrované vývojové prostředí (IDE), je vyvolána ladicího programu. To platí bez ohledu na to, jestli se v režimu ladění nebo prodejní zkompilovat kód.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Stop` příkaz pozastavit provádění pro každou iteraci prostřednictvím `For...Next` smyčky.  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [End – příkaz](../../../visual-basic/language-reference/statements/end-statement.md)
