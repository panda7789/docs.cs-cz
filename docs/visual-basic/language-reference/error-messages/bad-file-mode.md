---
title: Chybný režim souboru
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 534ea2d8316dc29cace798c5ad9b7697a290026f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409866"
---
# <a name="bad-file-mode"></a>Chybný režim souboru
Příkazy používané při manipulaci s obsahem souboru musí být vhodné pro režim, ve kterém byl soubor otevřen. Mezi možné příčiny patří:  
  
- `FilePutObject`Příkaz nebo `FileGetObject` určuje sekvenční soubor.  
  
- `Print`Příkaz určuje soubor otevřený pro jiný režim přístupu než `Output` nebo `Append` .  
  
- `Input`Příkaz určuje soubor otevřený pro jiný režim přístupu, než`Input`  
  
- Pokus o zápis do souboru určeného jen pro čtení.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se `FilePutObject` , že a že `FileGetObject` odkazují jenom na soubory otevřené pro `Random` nebo `Binary` Access.  
  
- Zajistěte, aby byl `Print` soubor otevřen `Output` pro `Append` přístup nebo režim přístupu. V takovém případě použijte jiný příkaz k umístění dat do souboru nebo soubor znovu otevřete v příslušném režimu.  
  
- Ujistěte se, že `Input` Určuje soubor, který je otevřen pro `Input` . V takovém případě použijte jiný příkaz k umístění dat do souboru nebo znovu otevřete soubor v odpovídajícím režimu.  
  
- Pokud zapisujete do souboru určeného jen pro čtení, změňte stav čtení/zápisu souboru nebo se do něj nepokoušíte zapisovat.  
  
- Použijte funkce, které jsou k dispozici v `My.Computer.FileSystem` objektu.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileSystem>
- [Řešení potíží: Čtení z textových souborů a zápis do nich](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
