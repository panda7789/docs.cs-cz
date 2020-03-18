---
title: -highentropyva (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: b710bb829f6a7591159d2f2e6bacc670d21c42d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606855"
---
# <a name="-highentropyva-c-compiler-options"></a>-highentropyva (C# Možnosti kompilátoru)
Možnost kompilátoru **-highentropyva** informuje jádro systému Windows, zda určitý spustitelný soubor podporuje randomizaci rozložení adresního prostoru vysoké entropie (ASLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Tato možnost určuje, že 64bitový spustitelný soubor nebo spustitelný soubor, který je označen možností kompilátoru [-platform:anycpu,](./platform-compiler-option.md) podporuje virtuální adresní prostor s vysokou entropie. Tato možnost je ve výchozím nastavení zakázána. Použijte **-highentropyva+** nebo **-highentropyva,** abyste ji povolili.  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-highentropyva** umožňuje kompatibilním verzím jádra Systému Windows používat vyšší stupně entropie při randomizaci rozložení adresního prostoru procesu jako součásti ASLR. Použití vyšších stupňů entropie znamená, že větší počet adres lze přidělit do oblastí paměti, jako jsou zásobníky a hromady. V důsledku toho je obtížnější odhadnout umístění určité oblasti paměti.  
  
 Když je zadána možnost kompilátoru **-highentropyva,** cílový spustitelný soubor a všechny moduly, na kterých závisí, musí být schopny zpracovat hodnoty ukazatele, které jsou větší než 4 gigabajty (GB), pokud jsou spuštěny jako 64bitový proces.
