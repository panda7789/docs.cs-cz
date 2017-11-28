---
title: /utf8output (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23c7c308865a6b6afb07443a42090fff3d9e2efb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="utf8output-visual-basic"></a>/utf8output (Visual Basic)
Zobrazí výstup kompilátoru pomocí kódování UTF-8.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Výchozí hodnota pro tuto možnost je `/utf8output-`, což znamená, že výstup kompilátoru nepoužívá kódování UTF-8. Určení `/utf8output` je stejné jako zadání `/utf8output+`.  
  
## <a name="remarks"></a>Poznámky  
 V některých konfiguracích mezinárodní výstupu kompilátoru nelze správně v konzole. V takových situacích použít `/utf8output` a přesměrujte výstup kompilátoru do souboru.  
  
> [!NOTE]
>  `/utf8output` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a přesměruje kompilátoru k zobrazení výstupu pomocí kódování UTF-8.  
  
```  
vbc /utf8output in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
