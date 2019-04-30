---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: c1824e4a086ecdd4b6a776bd6894f6e003d02867
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789000"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Potlačí zobrazení nápisu o autorských právech a informačních zpráv během kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud zadáte `-nologo`, kompilátor nezobrazuje o autorských právech banner. Ve výchozím nastavení `-nologo` není platná.  
  
> [!NOTE]
>  `-nologo` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a o autorských právech banner nezobrazí.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
