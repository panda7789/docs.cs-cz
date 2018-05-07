---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: e67fe05507c8cb3edd7f46cad19211ba11e3b054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
