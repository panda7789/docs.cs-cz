---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fef3f922d3089eaca1762ffe35fa38cfe94baf22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656312"
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic)
Určuje, zda spustitelný soubor 64-bit nebo jenom spustitelný soubor, která je označena kvalifikátorem [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) – možnost kompilátoru podporuje vysokou entropie místo rozložení náhodného přeskupování (technologie ASLR) adres.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Možnost je vypnuta ve výchozím nastavení nebo pokud zadáte `-highentropyva-`. Možnost zapnutý, pokud zadáte `-highentropyva` nebo `-highentropyva+`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud zadáte tuto možnost, můžete kompatibilní verze jádro systému Windows použít vyšší stupňů entropie při jádra randomizes rozložení prostoru adres procesu v rámci technologie ASLR. Pokud jádra používá vyšší stupňů entropie, oblasti paměti, jako je například zásobníky a haldách můžete přidělit větší počet adres. V důsledku toho je obtížnější uhádnout umístění paměti konkrétní oblasti.  
  
 Pokud možnost je na cílový spustitelný soubor a všechny moduly, na které závisí musí být schopen zpracování ukazatele hodnot, které jsou větší než 4 gigabajty (GB), pokud se tyto moduly se spustí jako 64bitové procesy.  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
