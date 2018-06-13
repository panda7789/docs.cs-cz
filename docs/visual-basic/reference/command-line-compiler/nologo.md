---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 011c9499eaa728588e6181e33a96dd75b4a7b84b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648538"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Potlačí zobrazení autorským banner a informační zprávy během kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud zadáte `-nologo`, kompilátor nemá zobrazovat nápis informující o autorských právech. Ve výchozím nastavení `-nologo` není funkční.  
  
> [!NOTE]
>  `-nologo` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a nemá zobrazovat nápis informující o autorských právech.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
