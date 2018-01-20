---
title: "-highentropyva (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d0b9a7a53545623ae5d5692b52973744adbcc299
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-highentropyva-c-compiler-options"></a>-highentropyva (možnosti kompilátoru C#)
**- Highentropyva** – možnost kompilátoru informuje jádro systému Windows, jestli konkrétní spustitelný soubor podporuje vysokou entropie místo rozložení náhodného přeskupování (technologie ASLR) adres.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Tato možnost určuje, že spustitelný soubor 64-bit nebo jenom spustitelný soubor, která je označena kvalifikátorem [-platform: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) – možnost kompilátoru podporuje virtuální adresní prostor vysoké šifrování. Tato možnost je ve výchozím nastavení vypnuta. Použití **- highentropyva +** nebo **- highentropyva** povolit.  
  
## <a name="remarks"></a>Poznámky  
 **- Highentropyva** možnost umožňuje kompatibilní verze používat vyšší stupňů entropii v rámci procesu náhodného řazení rozložení prostoru adres procesu v rámci technologie ASLR jádro systému Windows. Použití vyšší stupňů šifrování znamená, že větší počet adres může být přidělen k oblasti paměti, jako je například zásobníky a hald. V důsledku toho je obtížnější uhádnout umístění paměti konkrétní oblasti.  
  
 Když **- highentropyva** – možnost kompilátoru je zadán, cílový spustitelný soubor a všechny moduly, které závisí na musí být schopna zpracovávat ukazatel hodnoty, které jsou větší než 4 gigabajty (GB), když používají jako 64bitový proces.
