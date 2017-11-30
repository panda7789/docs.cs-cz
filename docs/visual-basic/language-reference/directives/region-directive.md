---
title: "#<a name=\"region-directive\"></a>Region – direktiva"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb308da6ad0ca6243f14e0d825ed7eb005d622bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="region-directive"></a>#Region – direktiva
Sbalí a skrytí sekcí kódu v souborech jazyka Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [#If... Then... #Else – direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Osnova](/visualstudio/ide/outlining)  
 [Postupy: sbalení a skrytí sekcí kódu](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
