---
title: "Chybný režim souboru"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a540135727eb97f4df5027e2ded7271e21bb4648
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-mode"></a>Chybný režim souboru
Příkazy, které jsou používány práce s obsahem souboru musí být vhodné pro režim, ve kterém byl soubor otevřít. Možné příčiny:  
  
-   A `FilePutObject` nebo `FileGetObject` příkaz určuje sekvenční soubor.  
  
-   A `Print` příkaz určuje soubor otevřít pro přístupovém režimu jiné než `Output` nebo `Append`.  
  
-   `Input` Příkaz určuje soubor otevřít pro přístupovém režimu jiné než`Input`  
  
-   Pokus o zápis do souboru jen pro čtení.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zajistěte, aby `FilePutObject` a `FileGetObject` jsou pouze odkazy na soubory otevřené pro `Random` nebo `Binary` přístup.  
  
-   Zajistěte, aby `Print` Určuje soubor otevřít pro buď `Output` nebo `Append` režim přístupu. Pokud ne, použít jiný příkaz umístit data v souboru nebo znovu otevřete soubor v odpovídající režim.  
  
-   Zajistěte, aby `Input` Určuje soubor otevřít pro `Input`. Pokud ne, použijte jiný příkaz umístit data v souboru nebo znovu otevřete soubor v odpovídající režim.  
  
-   Pokud píšete do souboru jen pro čtení, změňte stav pro čtení a zápis souboru nebo Nepokoušejte se do něj zapisovat.  
  
-   Používat funkce, které jsou k dispozici v `My.Computer.FileSystem` objektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [Řešení potíží: Čtení a zápis do textových souborů](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
