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
ms.openlocfilehash: 590ac27ebab881353a69077aabdf7a2def3396a6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967839"
---
# <a name="stop-statement-visual-basic"></a>Stop – příkaz (Visual Basic)
Pozastaví provádění kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete umístit `Stop` příkazy kdekoli v postupech k pozastavení provádění. Použití `Stop` příkaz je podobný nastavením zarážky v kódu.  
  
 `Stop` Příkaz pozastaví provádění, ale na rozdíl od `End`, ne zavřít všechny soubory, nebo zrušte všechny proměnné, pokud není nalezen v souboru zkompilovaného spustitelného souboru (.exe).  
  
> [!NOTE]
>  Pokud `Stop` příkaz dochází v kódu, který běží mimo integrované vývojové prostředí (IDE), ladicí program je vyvolán. To platí bez ohledu na to, zda byl zkompilován kódu v režimu ladění nebo maloobchodního prodeje.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Stop` příkaz k pozastavení provádění pro každou iteraci přes `For...Next` smyčky.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Viz také:
- [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)
