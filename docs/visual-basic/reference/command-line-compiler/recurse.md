---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd5dde46cdea67825b14a6f5fa96a82c8bab8d3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652419"
---
# <a name="-recurse"></a>-recurse
Zkompiluje soubory zdrojového kódu ve všech zadaný adresář nebo adresáři projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 Volitelné. Adresář, ve kterém chcete vyhledávání začít. Pokud není zadaný, začne vyhledávání v adresáři projektu.  
  
 `file`  
 Požadováno. Soubory, které chcete vyhledat. Zástupné znaky jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít zástupné znaky v názvu souboru pro kompilaci všechny odpovídající soubory v adresáři projektu bez použití `-recurse`. Pokud není zadán žádný název výstupního souboru, kompilátor základny název výstupního souboru na první vstupní soubor zpracovat. Obvykle se jedná o první soubor v seznamu souborů kompilovat při zobrazení podle abecedy. Z tohoto důvodu je nejlepší určit soubor výstupu pomocí `-out` možnost.  
  
> [!NOTE]
>  `-recurse` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje všechny soubory jazyka Visual Basic v aktuálním adresáři.  
  
```console
vbc *.vb  
```  
  
 Následující příkaz kompiluje všechny soubory jazyka Visual Basic v `Test\ABC` adresář a všechny adresáře níže a poté generuje `Test.ABC.dll`.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
