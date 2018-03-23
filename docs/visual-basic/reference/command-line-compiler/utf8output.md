---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97f90b39046aebe0cd15c7e033d8e588045491f7
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
Zobrazí výstup kompilátoru pomocí kódování UTF-8.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Výchozí hodnota pro tuto možnost je `-utf8output-`, což znamená, že výstup kompilátoru nepoužívá kódování UTF-8. Určení `-utf8output` je stejné jako zadání `-utf8output+`.  
  
## <a name="remarks"></a>Poznámky  
 V některých konfiguracích mezinárodní výstupu kompilátoru nelze správně v konzole. V takových situacích použít `-utf8output` a přesměrujte výstup kompilátoru do souboru.  
  
> [!NOTE]
>  `-utf8output` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a přesměruje kompilátoru k zobrazení výstupu pomocí kódování UTF-8.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
