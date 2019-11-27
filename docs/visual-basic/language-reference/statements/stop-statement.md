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
ms.openlocfilehash: 497c5f207b2228412411cc3eb01976564f82bd6c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346469"
---
# <a name="stop-statement-visual-basic"></a>Stop – příkaz (Visual Basic)
Pozastaví provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete umístit `Stop` příkazy kdekoli v postupech pro pozastavení provádění. Použití příkazu `Stop` je podobné jako nastavení zarážky v kódu.  
  
 Příkaz `Stop` pozastaví provádění, ale na rozdíl od `End`nezavře žádné soubory ani nevymaže žádné proměnné, pokud se nevyskytly v kompilovaném spustitelném souboru (. exe).  
  
> [!NOTE]
> Pokud je v kódu, který běží mimo integrované vývojové prostředí (IDE), nalezen příkaz `Stop`, je vyvolán ladicí program. To platí bez ohledu na to, zda byl kód zkompilován v režimu ladění nebo maloobchodu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá příkaz `Stop` k pozastavení provádění každé iterace prostřednictvím smyčky `For...Next`.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)
