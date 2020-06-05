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
ms.openlocfilehash: 68c898145bd8845c657b6ebb8776a3a9027c359c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404262"
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
 Nepovinný parametr. Text libovolného komentáře, který chcete zahrnout. Mezi `REM` klíčovým slovem and se vyžaduje mezera `comment` .  
  
## <a name="remarks"></a>Poznámky  
 Příkaz můžete umístit `REM` samostatně na řádek nebo ho můžete umístit na řádek za jiným příkazem. `REM`Příkaz musí být poslední příkaz na řádku. Pokud má jiný příkaz, `REM` musí být oddělen od tohoto příkazu mezerou.  
  
 Místo příkazu můžete použít jednoduchou uvozovku ( `'` ) `REM` . To platí bez ohledu na to, jestli váš komentář následuje za jiným příkazem na stejném řádku, nebo se nachází na řádku samostatně.  
  
> [!NOTE]
> Nelze pokračovat `REM` příkazem pomocí sekvence řádků pokračování řádku ( `_` ). Po zahájení komentáře kompilátor neověřuje znaky pro zvláštní význam. Pro Víceřádkový komentář použijte jiný `REM` příkaz nebo symbol komentáře ( `'` ) na každém řádku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `REM` příkaz, který se používá k zahrnutí vysvětlujících poznámek do programu. Také ukazuje alternativu použití jednoduchého znaku uvozovek ( `'` ) místo `REM` .  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také

- [Komentáře v kódu](../../programming-guide/program-structure/comments-in-code.md)
- [Postupy: Přerušení a kombinování příkazů v kódu](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
