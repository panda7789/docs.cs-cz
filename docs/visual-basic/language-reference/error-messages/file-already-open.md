---
title: "Soubor již je otevřen."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a>Soubor již je otevřen.
Někdy soubor musí být uzavřeny před jiné `FileOpen` nebo může dojít, jiná operace. Mezi možné příčiny této chyby patří:  
  
-   Režim sekvenční výstup `FileOpen` byla provedena operace pro soubor, který je již otevřeno  
  
-   Příkaz odkazuje na soubor otevřený.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zavřete soubor před provedením příkazu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
