---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 405b557568a736de3ddc3b51e265261222613131
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403028"
---
# <a name="-verbose"></a>-verbose
Způsobí, že kompilátor vyprodukuje Podrobné stavové a chybové zprávy.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Nepovinný parametr. Určení `-verbose` je stejné jako při zadání `-verbose+` , což způsobí, že kompilátor vygeneruje podrobné zprávy. Výchozí hodnota pro tuto možnost je `-verbose-` .  
  
## <a name="remarks"></a>Poznámky  
 `-verbose`Možnost zobrazí informace o celkovém počtu chyb vydaných kompilátorem, sestav, které sestavení načítá modul, a zobrazuje, které soubory jsou aktuálně kompilovány.  
  
> [!NOTE]
> Tato `-verbose` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a nasměruje kompilátor pro zobrazení podrobných informací o stavu.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
