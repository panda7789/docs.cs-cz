---
title: /verbose
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5480f828fa1f0b6d71fa649bf44513ce806bb440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="verbose"></a>/verbose
Způsobí, že kompilátoru vytvoření podrobné zprávy o stavu a chyb.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Určení `/verbose` je stejné jako zadání `/verbose+`, což způsobí, že kompilátoru pro generování podrobné zprávy. Výchozí hodnota pro tuto možnost je `/verbose-`.  
  
## <a name="remarks"></a>Poznámky  
 `/verbose` Možnost zobrazí informace o celkový počet chyb vystavený kompilátor, sestavy, které sestavení jsou načítány pomocí modulu a soubory, které jsou nyní kompilována.  
  
> [!NOTE]
>  `/verbose` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a přesměruje kompilátoru zobrazíte podrobné stavové informace.  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
