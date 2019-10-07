---
title: -Utf8Output – (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: adcb518cbe8397549c3ae3b3a8ca9f0ecf9dc38e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004669"
---
# <a name="-utf8output-visual-basic"></a>-Utf8Output – (Visual Basic)
Zobrazí výstup kompilátoru pomocí kódování UTF-8.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Výchozí hodnota pro tuto možnost je `-utf8output-`, což znamená, že výstup kompilátoru nepoužívá kódování UTF-8. Zadání `-utf8output` se shoduje s určením `-utf8output+`.  
  
## <a name="remarks"></a>Poznámky  
 V některých mezinárodních konfiguracích nelze výstup kompilátoru v konzole zobrazit správně. V takových situacích použijte `-utf8output` a přesměrujte výstup kompilátoru do souboru.  
  
> [!NOTE]
> Možnost `-utf8output` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a nasměruje kompilátor, aby zobrazoval výstup pomocí kódování UTF-8.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
