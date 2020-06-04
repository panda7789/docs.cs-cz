---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 0a16cdc535de5ed0619bf080bb4637449b11cfef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403054"
---
# <a name="-utf8output-visual-basic"></a>-Utf8Output – (Visual Basic)
Zobrazí výstup kompilátoru pomocí kódování UTF-8.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Nepovinný parametr. Výchozí hodnota pro tuto možnost je `-utf8output-` , což znamená, že výstup kompilátoru nepoužívá kódování UTF-8. Určení `-utf8output` je stejné jako zadání `-utf8output+` .  
  
## <a name="remarks"></a>Poznámky  
 V některých mezinárodních konfiguracích nelze výstup kompilátoru v konzole zobrazit správně. V takových situacích použijte `-utf8output` a přesměrujte výstup kompilátoru do souboru.  
  
> [!NOTE]
> Tato `-utf8output` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a nasměruje kompilátor pro zobrazení výstupu pomocí kódování UTF-8.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
