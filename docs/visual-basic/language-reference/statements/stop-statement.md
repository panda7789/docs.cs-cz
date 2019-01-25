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
ms.openlocfilehash: fa9a1942903dff6f673d87b67ebcad047a410425
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624779"
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
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)
