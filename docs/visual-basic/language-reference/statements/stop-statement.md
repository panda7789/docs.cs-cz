---
title: Stop – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: 955a3b6a2f7dc1d0e9823ed6d500ab7f7f9fe5b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)
