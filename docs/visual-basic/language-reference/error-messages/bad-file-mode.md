---
title: Chybný režim souboru
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 1d85f49ce0aed44dea12c9ba16135425e6e2e431
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565745"
---
# <a name="bad-file-mode"></a>Chybný režim souboru
Příkazy používané práce s obsahem souboru musí být příslušný režim, ve kterém soubor byl otevřen. Mezi možné příčiny patří:  
  
-   A `FilePutObject` nebo `FileGetObject` příkaz určuje sekvenčního souboru.  
  
-   A `Print` příkaz určuje soubor otevřen pro přístupový režim jiné než `Output` nebo `Append`.  
  
-   `Input` Příkaz určuje soubor otevřen pro přístupový režim jiné než `Input`  
  
-   Pokus o zápis do souboru jen pro čtení.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ujistěte se, že `FilePutObject` a `FileGetObject` pouze odkazují na soubory otevřené pro `Random` nebo `Binary` přístup.  
  
-   Ujistěte se, že `Print` Určuje soubor otevřen pro buď `Output` nebo `Append` přístupovém režimu. V opačném případě použijte jiný příkaz umístit data v souboru nebo znovu otevřete soubor v odpovídající režim.  
  
-   Ujistěte se, že `Input` Určuje soubor otevřen pro `Input`. Pokud ne, použijte jiný příkaz umístit data souboru nebo znovu otevřete soubor v odpovídající režim.  
  
-   Při psaní do souboru jen pro čtení, změňte stav čtení a zápis souboru nebo Nepokoušejte se do ní zapisovat.  
  
-   Použití funkce, která je dostupná v `My.Computer.FileSystem` objektu.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileSystem>
- [Řešení potíží: Čtení a zápis do textových souborů](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
