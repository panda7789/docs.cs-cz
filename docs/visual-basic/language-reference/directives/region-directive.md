---
title: '#Region – direktiva (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: db8063cf06ad0735bb4d9290c60548f7ff9af217
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611940"
---
# <a name="region-directive"></a>#Region – direktiva
Sbalí a skryje části kódu v souborech Visual Basicu.  
  
## <a name="syntax"></a>Syntaxe  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`identifier_string`|Povinný parametr. Řetězec, který funguje jako název oblasti, když je sbalené. Ve výchozím nastavení je sbalený oblastech.|  
|`#End Region`|Ukončuje `#Region` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Použití `#Region` směrnice určit blok kódu, který rozbalit nebo sbalit při použití funkce sbalování z editoru kódu sady Visual Studio. Můžete umístit, nebo *vnořit*, oblastem v jiných oblastech, které chcete seskupit podobné oblastech.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `#Region` směrnice.  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Sbalení](/visualstudio/ide/outlining)
- [Postupy: Sbalení a skrytí sekcí kódu](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
