---
title: -quiet
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0ed08e013f088f512ae915daa9aeb2fa6b249b0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-quiet"></a>-quiet
Zabrání zobrazení kódu syntaxe související chyby a upozornění kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-quiet  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `-quiet` není funkční. Když kompilátor ohlásí syntaxe související chyby nebo upozornění, také výstupy řádku ze zdrojového kódu. Pro aplikace, které analyzovat výstupu kompilátoru může být pohodlnější kompilátor pro výstup jenom text diagnostiky.  
  
 V následujícím příkladu `Module1` výstupy chybu, která obsahuje zdrojový kód při kompilaci bez `-quiet`.  
  
```vb  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 Výstup:  
 
```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
``` 
 Kompilované s `-quiet`, kompilátor výstupy jenom následující:  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  `-quiet` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a nezobrazí kód pro diagnostiku související syntaxe kompilátoru:  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
