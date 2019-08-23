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
ms.openlocfilehash: a617038ec51d98c62b6cf7e3c124c8af01305bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957624"
---
# <a name="stop-statement-visual-basic"></a>Stop – příkaz (Visual Basic)
Pozastaví provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Poznámky  
 Příkazy lze umístit `Stop` kdekoli v postupech pro pozastavení provádění. `Stop` Použití příkazu je podobné jako nastavení zarážky v kódu.  
  
 Příkaz pozastaví provádění, ale na rozdíl od `End`, neuzavře žádné soubory ani nevymaže žádné proměnné, pokud se nevyskytly v kompilovaném spustitelném souboru (. exe). `Stop`  
  
> [!NOTE]
> Je-li příkaz nalezen v kódu, který je spuštěn mimo integrované vývojové prostředí (IDE), je vyvolán ladicí program. `Stop` To platí bez ohledu na to, zda byl kód zkompilován v režimu ladění nebo maloobchodu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se `Stop` používá příkaz pro pozastavení provádění každé iterace `For...Next` prostřednictvím smyčky.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)
