---
title: Alias – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: a7f67224c5d26816bdc1974dc4aa82d796c41284
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349151"
---
# <a name="alias-clause-visual-basic"></a>Alias – klauzule (Visual Basic)
Označuje, že externí procedura má jiný název ve své knihovně DLL.  
  
## <a name="remarks"></a>Poznámky  
 Klíčové slovo `Alias` lze použít v tomto kontextu:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 V následujícím příkladu je klíčové slovo `Alias` použito k poskytnutí názvu funkce v souboru advapi32. dll `GetUserNameA`, který `getUserName` je použit místo v tomto příkladu. Funkce `getUserName` je volána v sub `getUser`, která zobrazuje název aktuálního uživatele.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Viz také:

- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
