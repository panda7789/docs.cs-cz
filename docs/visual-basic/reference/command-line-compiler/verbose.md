---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5f257fce67d8e348b69404411c12ded785cfd68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652126"
---
# <a name="-verbose"></a>-verbose
Způsobí, že kompilátoru vytvoření podrobné zprávy o stavu a chyb.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Určení `-verbose` je stejné jako zadání `-verbose+`, což způsobí, že kompilátoru pro generování podrobné zprávy. Výchozí hodnota pro tuto možnost je `-verbose-`.  
  
## <a name="remarks"></a>Poznámky  
 `-verbose` Možnost zobrazí informace o celkový počet chyb vystavený kompilátor, sestavy, které sestavení jsou načítány pomocí modulu a soubory, které jsou nyní kompilována.  
  
> [!NOTE]
>  `-verbose` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a přesměruje kompilátoru zobrazíte podrobné stavové informace.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
