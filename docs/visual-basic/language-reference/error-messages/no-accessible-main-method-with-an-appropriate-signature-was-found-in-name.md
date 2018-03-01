---
title: "Žádné dostupné & č. 39; Hlavní & č. 39; nebyla nalezena metoda s odpovídajícím podpisem v & č. 39; &lt;název&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6a2d66c860b72bd3ef59c02f548ac563fab6b8c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a>Žádné dostupné & č. 39; Hlavní & č. 39; nebyla nalezena metoda s odpovídajícím podpisem v & č. 39; &lt;název&gt;& č. 39;
Aplikace příkazového řádku musí mít `Sub Main` definované. `Main`musí být deklarována jako `Public Shared` Pokud je definována v třídě nebo jako `Public` Pokud definovaná v modulu.  
  
 **ID chyby:** BC30737  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Definování `Public Sub Main` postup pro váš projekt. Deklarujte ji jako `Shared` jenom v případě můžete definovat uvnitř třídy.  
  
## <a name="see-also"></a>Viz také  
 [Struktura programu v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
