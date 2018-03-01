---
title: "Úvodní & č. 39;. & č. 39; nebo & č. 39;! & č. 39; může být použit pouze uvnitř a & č. 39; S & č. 39; příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 961f2d737123ab68b200d5fc7658cb81291a5de6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>Úvodní & č. 39;. & č. 39; nebo & č. 39;! & č. 39; může být použit pouze uvnitř a & č. 39; S & č. 39; příkaz
Tečka (.) nebo vykřičník (!), který není uvnitř `With` bloku probíhá, aniž by výraz na levé straně. Přístup ke členu (`.`) a přístup ke členu slovníku (`!`) vyžadují zadání elementu, který obsahuje člen výrazu. Ta musí okamžitě zobrazí nalevo přistupujícího objektu nebo jako cíl `With` bloku obsahující přístup ke členu.  
  
 **ID chyby:** BC30157  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že `With` bloku je správně naformátován.  
  
2.  Pokud není žádná `With` blokovat, přidejte výraz nalevo od přistupujícího objektu, která vyhodnotí definovaný element obsahující člena.  
  
## <a name="see-also"></a>Viz také  
 [Speciální znaky v kódu](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [S... End With – příkaz](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
