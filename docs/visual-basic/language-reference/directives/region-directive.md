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
ms.openlocfilehash: 4cf9b103486378d001b588aa285f590980b51bb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343795"
---
# <a name="region-directive"></a>#Region – direktiva

Sbalí a skryje části kódu v souborech Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`identifier_string`|Požadováno. Řetězec, který slouží jako název oblasti při sbalení. Oblasti jsou ve výchozím nastavení sbaleny.|  
|`#End Region`|Ukončí blok `#Region`.|  
  
## <a name="remarks"></a>Poznámky  

 Pomocí direktivy `#Region` můžete určit blok kódu, který se má rozbalit nebo sbalit při použití funkce sbalení editoru Visual Studio Code. Můžete umístit nebo *vnořovat*oblasti v rámci jiných oblastí a seskupovat podobné oblasti dohromady.  
  
## <a name="example"></a>Příklad  

 V tomto příkladu se používá direktiva `#Region`.  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Sbalení](/visualstudio/ide/outlining)
- [Postupy: Sbalení a skrytí sekcí kódu](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
