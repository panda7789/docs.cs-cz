---
description: -HIGHENTROPYVA (možnosti kompilátoru C#)
title: -HIGHENTROPYVA (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2c2e2780693a89072c4bb55b318be94089bf3ced
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125654"
---
# <a name="-highentropyva-c-compiler-options"></a>-HIGHENTROPYVA (možnosti kompilátoru C#)
Možnost kompilátoru **-HIGHENTROPYVA** přikáže jádru systému Windows, zda určitý spustitelný soubor podporuje náhodné vygenerování rozložení adresního prostoru (ASLR) vysoké entropie.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Tato možnost určuje, že 64 spustitelný soubor nebo spustitelný soubor, který je označený pomocí možnosti kompilátoru [-Platform: anycpu](./platform-compiler-option.md) , podporuje virtuální adresní prostor s vysokou entropií. Možnost je ve výchozím nastavení zakázána. K povolení použijte **-HIGHENTROPYVA +** nebo **-HIGHENTROPYVA** .  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-HIGHENTROPYVA** umožňuje kompatibilní verze jádra Windows pro použití vyšších stupňů entropie při náhodném rozložení adresního prostoru procesu jako součást ASLR. Použití vyšších stupňů entropie znamená, že větší počet adres může být přidělen do oblastí paměti, jako jsou zásobníky a haldy. V důsledku toho je obtížné odhadnout umístění konkrétní oblasti paměti.  
  
 Je-li zadána možnost kompilátoru **-HIGHENTROPYVA** , musí být cílový spustitelný soubor a všechny moduly, na kterých závisí, schopny zpracovat hodnoty ukazatele, které jsou větší než 4 gigabajty (GB), pokud jsou spuštěny jako 64 proces.
