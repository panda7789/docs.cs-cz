---
title: -HIGHENTROPYVA (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: b710bb829f6a7591159d2f2e6bacc670d21c42d1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606855"
---
# <a name="-highentropyva-c-compiler-options"></a>-HIGHENTROPYVA (C# možnosti kompilátoru)
Možnost kompilátoru **-HIGHENTROPYVA** přikáže jádru systému Windows, zda určitý spustitelný soubor podporuje náhodné vygenerování rozložení adresního prostoru (ASLR) vysoké entropie.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Tato možnost určuje, že 64 spustitelný soubor nebo spustitelný soubor, který je označený pomocí možnosti kompilátoru [-Platform: anycpu](./platform-compiler-option.md) , podporuje virtuální adresní prostor s vysokou entropií. Možnost je ve výchozím nastavení zakázána. K povolení použijte **-HIGHENTROPYVA +** nebo **-HIGHENTROPYVA** .  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-HIGHENTROPYVA** umožňuje kompatibilní verze jádra Windows pro použití vyšších stupňů entropie při náhodném rozložení adresního prostoru procesu jako součást ASLR. Použití vyšších stupňů entropie znamená, že větší počet adres může být přidělen do oblastí paměti, jako jsou zásobníky a haldy. V důsledku toho je obtížné odhadnout umístění konkrétní oblasti paměti.  
  
 Je-li zadána možnost kompilátoru **-HIGHENTROPYVA** , musí být cílový spustitelný soubor a všechny moduly, na kterých závisí, schopny zpracovat hodnoty ukazatele, které jsou větší než 4 gigabajty (GB), pokud jsou spuštěny jako 64 proces.
