---
title: "Příkaz nemůže ukončit blok mimo řádek & č. 39; Pokud & č. 39; příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73fe3eb44e904366db7d505bbe8c5fef461eb78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>Příkaz nemůže ukončit blok mimo řádek & č. 39; Pokud & č. 39; příkaz
Jeden řádek `If` příkaz obsahuje několik příkazů oddělené dvojtečkou (:), z nichž jeden je `End` příkaz pro řídicí blok mimo jeden řádek `If`. Jeden řádek `If` příkazy se nedoporučuje používat `End If` příkaz.  
  
 **ID chyby:** BC32005  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přesunout jednom řádku `If` příkaz mimo řídicí blok, který obsahuje `End If` příkaz.  
  
## <a name="see-also"></a>Viz také  
 [If... Potom... Else – příkaz](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
