---
title: REM – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 16149ce42e3476cf07a62298f83734fee9ec7253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957761"
---
# <a name="rem-statement-visual-basic"></a>REM – příkaz (Visual Basic)
Slouží k zahrnutí vysvětlujících poznámek do zdrojového kódu programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Součásti  
 `comment`  
 Volitelný parametr. Text libovolného komentáře, který chcete zahrnout. Mezi `REM` klíčovým slovem and `comment`se vyžaduje mezera.  
  
## <a name="remarks"></a>Poznámky  
 `REM` Příkaz můžete umístit samostatně na řádek nebo ho můžete umístit na řádek za jiným příkazem. `REM` Příkaz musí být poslední příkaz na řádku. Pokud má jiný příkaz, `REM` musí být oddělen od tohoto příkazu mezerou.  
  
 Místo příkazu můžete použít jednoduchou uvozovku (`'`). `REM` To platí bez ohledu na to, jestli váš komentář následuje za jiným příkazem na stejném řádku, nebo se nachází na řádku samostatně.  
  
> [!NOTE]
> Nelze pokračovat `REM` příkazem pomocí sekvence řádků pokračování řádku (`_`). Po zahájení komentáře kompilátor neověřuje znaky pro zvláštní význam. Pro Víceřádkový komentář použijte jiný `REM` příkaz nebo symbol komentáře (`'`) na každém řádku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `REM` příkaz, který se používá k zahrnutí vysvětlujících poznámek do programu. Také ukazuje alternativu použití jednoduchého znaku uvozovek (`'`) `REM`místo.  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Komentáře v kódu](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [Postupy: Přerušení a kombinování příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
