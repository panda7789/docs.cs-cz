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
ms.openlocfilehash: cd53a6079c1564a8c73a0a1a6273fc166d18d3e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409933"
---
# <a name="region-directive"></a>#Region – direktiva

Sbalí a skryje části kódu v souborech Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`identifier_string`|Povinná hodnota. Řetězec, který slouží jako název oblasti při sbalení. Oblasti jsou ve výchozím nastavení sbaleny.|  
|`#End Region`|Ukončí `#Region` blok.|  
  
## <a name="remarks"></a>Poznámky  

 Pomocí `#Region` direktivy určete blok kódu, který se má rozbalit nebo sbalit při použití funkce sbalení editoru Visual Studio Code. Můžete umístit nebo *vnořovat*oblasti v rámci jiných oblastí a seskupovat podobné oblasti dohromady.  
  
## <a name="example"></a>Příklad  

 V tomto příkladu se používá `#Region` direktiva.  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Viz také

- [#If... Then... #Else – direktivy](if-then-else-directives.md)
- [Sbalování](/visualstudio/ide/outlining)
- [Postupy: Sbalení a skrytí sekcí kódu](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
