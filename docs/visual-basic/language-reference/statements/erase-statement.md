---
title: Erase – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 6d2052ceccbecd772c4e4bb18052aed74223a36e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343704"
---
# <a name="erase-statement-visual-basic"></a>Erase – příkaz (Visual Basic)
Slouží k uvolnění proměnných pole a navrácení paměti používané pro jejich elementy.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>Součásti  
 `arraylist`  
 Požadováno. Seznam proměnných pole, které mají být smazány. Více proměnných je odděleno čárkami.  
  
## <a name="remarks"></a>Poznámky  
 Příkaz `Erase` se může vyskytovat pouze na úrovni procedury. To znamená, že můžete uvolnit pole v proceduře, ale ne na úrovni třídy nebo modulu.  
  
 Příkaz `Erase` je ekvivalentní k přiřazování `Nothing` na každou proměnnou pole.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použit příkaz `Erase` pro vymazání dvou polí a uvolnění paměti (v uvedeném pořadí) paměti (1000 a 100 prvků úložiště). Příkaz `ReDim` potom přiřadí novou instanci pole k trojrozměrnému poli.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Viz také:

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Příkaz ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
