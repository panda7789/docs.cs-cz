---
title: -highentropyva (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2ff63ddc48a4f5c4287fe1badb092a1db93f68dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662852"
---
# <a name="-highentropyva-c-compiler-options"></a>-highentropyva (C# Compiler Options)
**- Highentropyva** – možnost kompilátoru říká jádra Windows, jestli konkrétní spustitelný soubor podporuje vysokou entropie adresu místo rozložení náhodné (ASLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Tato možnost určuje, že spustitelný soubor 64-bit nebo spustitelný soubor, který je označen [-platform: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) – možnost kompilátoru podporuje vysokou entropie virtuálního adresového prostoru. Možnost je ve výchozím nastavení zakázána. Použití **- highentropyva +** nebo **- highentropyva** ho chcete povolit.  
  
## <a name="remarks"></a>Poznámky  
 **- Highentropyva** možnost povolí kompatibilní verze jádra Windows používat vyšší stupeň entropie v rámci procesu náhodného řazení rozložení prostoru adres procesu jako součást technologie ASLR. Použitím vyšší stupeň entropie znamená, že větší počet adres je možné přidělit paměti oblastech, jako je zásobníky a haldy. V důsledku toho je obtížnější uhádnout umístění konkrétní paměťové oblasti.  
  
 Když **- highentropyva** – možnost kompilátoru je zadán, cílový spustitelný soubor a všechny moduly, které závisí na musí být schopna zpracovávat hodnoty ukazatele, které jsou větší než 4 gigabajty (GB) spuštěná jako 64bitový proces.
