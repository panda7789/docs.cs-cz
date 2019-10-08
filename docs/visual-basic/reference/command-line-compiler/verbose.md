---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 8c5bc1d2ce331b8fe9461f91d64fbeab5a070b59
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004973"
---
# <a name="-verbose"></a>-verbose
Způsobí, že kompilátor vyprodukuje Podrobné stavové a chybové zprávy.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Zadání `-verbose` je stejné jako určení `-verbose+`, což způsobí, že kompilátor vygeneruje podrobné zprávy. Výchozí hodnota pro tuto možnost je `-verbose-`.  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-verbose` zobrazí informace o celkovém počtu chyb vydaných kompilátorem, sestav, které sestavení načítá modul, a zobrazuje, které soubory jsou aktuálně kompilovány.  
  
> [!NOTE]
> Možnost `-verbose` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a nasměruje kompilátor, aby zobrazoval podrobné informace o stavu.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
