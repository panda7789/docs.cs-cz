---
title: Vstup za koncem souboru
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: abd5f5c6e5df262d1deadd74f0a146a8d436ceb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="input-past-end-of-file"></a>Vstup za koncem souboru
Buď `Input` příkaz je čtení ze souboru, který je prázdný nebo ve které se používá všechna data, nebo jste použili `EOF` funkce souborem otevřen pro binární.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Použití `EOF` funkce bezprostředně před `Input` příkaz pro zjištění konec souboru.  
  
2.  Pokud soubor je otevřen pro binární, použijte `Seek` a `Loc`.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
