---
title: Vstup za koncem souboru
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 5da14c7a28ecdcd023fc6439cb6ed64444c1183b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768550"
---
# <a name="input-past-end-of-file"></a>Vstup za koncem souboru
Buď `Input` příkazu je čtení ze souboru, který je prázdný nebo ve kterém se používá všechna data nebo jste použili `EOF` funkce se souborem otevření pro binární přístup.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Použití `EOF` funkce bezprostředně před `Input` příkaz k zjištění konce souboru.  
  
2. Pokud je soubor otevřen pro binární přístup, použijte `Seek` a `Loc`.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
