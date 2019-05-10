---
title: Soubor již je otevřen.
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 8ec878e04b0128c997c5be51d2c714d55abcde8c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665122"
---
# <a name="file-already-open"></a>Soubor již je otevřen.
Někdy musí zavřít soubor před jiný `FileOpen` nebo může dojít k jiné operace. Mezi možné příčiny této chyby patří:  
  
- Režim sekvenční výstupu `FileOpen` byla provedena operace pro soubor, který je již otevřen  
  
- Příkaz odkazuje na otevřený soubor.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zavřete soubor před provedením příkazu.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
