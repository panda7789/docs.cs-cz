---
title: Alias – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 84c8f39e632eebbe5382492669820910b38bc360
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839740"
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
