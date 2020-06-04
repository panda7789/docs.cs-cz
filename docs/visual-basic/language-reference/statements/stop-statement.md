---
title: Stop – příkaz
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
ms.openlocfilehash: 2ef1e2f9045e5509e11557c9fdaf3edd2786b72c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404223"
---
# <a name="stop-statement-visual-basic"></a>Stop – příkaz (Visual Basic)
Pozastaví provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Poznámky  
 Příkazy lze umístit `Stop` kdekoli v postupech pro pozastavení provádění. Použití `Stop` příkazu je podobné jako nastavení zarážky v kódu.  
  
 `Stop`Příkaz pozastaví provádění, ale na rozdíl od `End` , neuzavře žádné soubory ani nevymaže žádné proměnné, pokud se nevyskytly v kompilovaném spustitelném souboru (. exe).  
  
> [!NOTE]
> Je `Stop` -li příkaz nalezen v kódu, který je spuštěn mimo integrované vývojové prostředí (IDE), je vyvolán ladicí program. To platí bez ohledu na to, zda byl kód zkompilován v režimu ladění nebo maloobchodu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá `Stop` příkaz pro pozastavení provádění každé iterace prostřednictvím `For...Next` smyčky.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Viz také

- [Příkaz end](end-statement.md)
