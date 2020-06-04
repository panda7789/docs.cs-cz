---
title: Erase – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 31aeaf822bc9c1de59a5c5f68406c6521216ae0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404716"
---
# <a name="erase-statement-visual-basic"></a>Erase – příkaz (Visual Basic)
Slouží k uvolnění proměnných pole a navrácení paměti používané pro jejich elementy.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>Součásti  
 `arraylist`  
 Povinná hodnota. Seznam proměnných pole, které mají být smazány. Více proměnných je odděleno čárkami.  
  
## <a name="remarks"></a>Poznámky  
 `Erase`Příkaz se může vyskytovat pouze na úrovni procedury. To znamená, že můžete uvolnit pole v proceduře, ale ne na úrovni třídy nebo modulu.  
  
 `Erase`Příkaz je ekvivalentní k přiřazení `Nothing` každé proměnné pole.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Erase` příkaz k vymazání dvou polí a uvolnění paměti 100 1000 (v uvedeném pořadí). `ReDim`Příkaz následně přiřadí novou instanci pole trojrozměrnému poli.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Viz také

- [Nothing](../nothing.md)
- [ReDim – příkaz](redim-statement.md)
