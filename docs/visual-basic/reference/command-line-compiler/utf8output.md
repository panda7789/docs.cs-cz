---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 753c92cdf2124ee7fb1b471c7bc543b6db6f3daa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653582"
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
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
