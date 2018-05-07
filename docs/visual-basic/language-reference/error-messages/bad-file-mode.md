---
title: Chybný režim souboru
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: bccbbbeb79f38790a4664b0152ca3378fb55448d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="bad-file-mode"></a>Chybný režim souboru
Příkazy, které jsou používány práce s obsahem souboru musí být vhodné pro režim, ve kterém byl soubor otevřít. Možné příčiny:  
  
-   A `FilePutObject` nebo `FileGetObject` příkaz určuje sekvenční soubor.  
  
-   A `Print` příkaz určuje soubor otevřít pro přístupovém režimu jiné než `Output` nebo `Append`.  
  
-   `Input` Příkaz určuje soubor otevřít pro přístupovém režimu jiné než `Input`  
  
-   Pokus o zápis do souboru jen pro čtení.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zajistěte, aby `FilePutObject` a `FileGetObject` jsou pouze odkazy na soubory otevřené pro `Random` nebo `Binary` přístup.  
  
-   Zajistěte, aby `Print` Určuje soubor otevřít pro buď `Output` nebo `Append` režim přístupu. Pokud ne, použít jiný příkaz umístit data v souboru nebo znovu otevřete soubor v odpovídající režim.  
  
-   Zajistěte, aby `Input` Určuje soubor otevřít pro `Input`. Pokud ne, použijte jiný příkaz umístit data v souboru nebo znovu otevřete soubor v odpovídající režim.  
  
-   Pokud píšete do souboru jen pro čtení, změňte stav pro čtení a zápis souboru nebo Nepokoušejte se do něj zapisovat.  
  
-   Používat funkce, které jsou k dispozici v `My.Computer.FileSystem` objektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [Řešení potíží: Čtení z textových souborů a zápis do nich](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
