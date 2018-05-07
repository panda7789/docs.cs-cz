---
title: '#Region – direktiva'
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
ms.openlocfilehash: d25871140ef0674c013fc70d1306b2b4d0858556
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="region-directive"></a>#Region – direktiva
Sbalí a skrytí sekcí kódu v souborech jazyka Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`identifier_string`|Požadováno. Řetězec, který funguje jako název oblasti, když je sbalená. Ve výchozím nastavení jsou sbaleny oblasti.|  
|`#End Region`|Ukončí `#Region` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Použití `#Region` – direktiva blok kódu rozbalit nebo sbalit, když používáte funkci osnovy z editoru kódu sady Visual Studio. Můžete umístit, nebo *vnořit*, oblastem v jiných oblastech chcete seskupit podobné oblasti.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `#Region` – direktiva.  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Sbalení](/visualstudio/ide/outlining)  
 [Postupy: Sbalení a skrytí sekcí kódu](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
