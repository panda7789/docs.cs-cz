---
title: Alias – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 3b1a66ecfd3c023a12ac62191ca3671a195b45a6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978225"
---
# <a name="alias-clause-visual-basic"></a>Alias – klauzule (Visual Basic)
Označuje, že externí procedura má jiný název ve své DLL.  
  
## <a name="remarks"></a>Poznámky  
 `Alias` – Klíčové slovo lze použít v tomto kontextu:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 V následujícím příkladu `Alias` – klíčové slovo se používá k poskytnutí názvu funkce v advapi32.dll, `GetUserNameA`, který `getUserName` je použito místo v tomto příkladu. Funkce `getUserName` je volána v dílčí `getUser`, která zobrazí jméno aktuálního uživatele.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Viz také:
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
