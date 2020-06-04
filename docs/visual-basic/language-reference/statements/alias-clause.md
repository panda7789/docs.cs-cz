---
title: Alias – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: c28e931a376b20b2058a7187551405cd9523d4fe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408468"
---
# <a name="alias-clause-visual-basic"></a>Alias – klauzule (Visual Basic)
Označuje, že externí procedura má jiný název ve své knihovně DLL.  
  
## <a name="remarks"></a>Poznámky  
 `Alias`Klíčové slovo lze použít v tomto kontextu:  
  
 [Declare – příkaz](declare-statement.md)  
  
 V následujícím příkladu se `Alias` klíčové slovo používá k poskytnutí názvu funkce v advapi32. dll, `GetUserNameA` která `getUserName` je použita místo v tomto příkladu. Funkce `getUserName` je volána v sub `getUser` , která zobrazuje název aktuálního uživatele.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Viz také

- [Klíčová slova](../keywords/index.md)
