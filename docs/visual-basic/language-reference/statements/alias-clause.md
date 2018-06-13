---
title: Alias – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 62b34f5860b35104b6a8caa82c359383999dd61b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599171"
---
# <a name="alias-clause-visual-basic"></a>Alias – klauzule (Visual Basic)
Určuje, že externí procedura má jiný název v jeho knihovny DLL.  
  
## <a name="remarks"></a>Poznámky  
 `Alias` – Klíčové slovo lze použít v tomto kontextu:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 V následujícím příkladu `Alias` – klíčové slovo slouží k zadání názvu funkce v advapi32.dll, `GetUserNameA`, že `getUserName` se v tomto příkladu používá místě. Funkce `getUserName` je volána v dílčí `getUser`, který zobrazí název aktuálního uživatele.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
