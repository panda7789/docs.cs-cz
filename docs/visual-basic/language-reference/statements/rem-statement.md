---
title: REM – příkaz
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
ms.openlocfilehash: bdde4beae242c3175b02cd2af252babb850416f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346733"
---
# <a name="rem-statement-visual-basic"></a>REM – příkaz (Visual Basic)
Slouží k zahrnutí vysvětlujících poznámek do zdrojového kódu programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Součásti  
 `comment`  
 Volitelná. Text libovolného komentáře, který chcete zahrnout. Mezi klíčovým slovem `REM` a `comment`se vyžaduje mezera.  
  
## <a name="remarks"></a>Poznámky  
 Příkaz `REM` můžete umístit na řádek, nebo ho můžete umístit na řádek za jiným příkazem. Příkaz `REM` musí být poslední příkaz na řádku. Pokud se tento příkaz řídí jiným příkazem, `REM` musí být od tohoto příkazu oddělen mezerou.  
  
 Místo `REM`můžete použít jednoduchou uvozovku (`'`). To platí bez ohledu na to, jestli váš komentář následuje za jiným příkazem na stejném řádku, nebo se nachází na řádku samostatně.  
  
> [!NOTE]
> Příkaz `REM` nelze pokračovat pomocí posloupnosti pokračování řádku (`_`). Po zahájení komentáře kompilátor neověřuje znaky pro zvláštní význam. Pro Víceřádkový komentář použijte jiný příkaz `REM` nebo symbol komentáře (`'`) na každém řádku.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje příkaz `REM`, který se používá k zahrnutí vysvětlujících poznámek do programu. Také ukazuje alternativu použití jednoduchého znaku pro uvozovky (`'`) místo `REM`.  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Komentáře v kódu](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [Postupy: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
