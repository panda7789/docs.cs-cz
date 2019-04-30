---
title: Soubor již je otevřen.
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 401801c7c9072ce11f9eafdb84f2b377669ae545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802645"
---
# <a name="file-already-open"></a>Soubor již je otevřen.
Někdy musí zavřít soubor před jiný `FileOpen` nebo může dojít k jiné operace. Mezi možné příčiny této chyby patří:  
  
- Režim sekvenční výstupu `FileOpen` byla provedena operace pro soubor, který je již otevřen  
  
- Příkaz odkazuje na otevřený soubor.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zavřete soubor před provedením příkazu.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
