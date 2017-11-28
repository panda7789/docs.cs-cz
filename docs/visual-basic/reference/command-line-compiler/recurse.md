---
title: /recurse
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb69c7c44dcc2e8da5eb8a76f7d22f936a6d948f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="recurse"></a>/recurse
Zkompiluje soubory zdrojového kódu ve všech zadaný adresář nebo adresáři projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 Volitelné. Adresář, ve kterém chcete vyhledávání začít. Pokud není zadaný, začne vyhledávání v adresáři projektu.  
  
 `file`  
 Požadováno. Soubory, které chcete vyhledat. Zástupné znaky jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít zástupné znaky v názvu souboru pro kompilaci všechny odpovídající soubory v adresáři projektu bez použití `/recurse`. Pokud není zadán žádný název výstupního souboru, kompilátor základny název výstupního souboru na první vstupní soubor zpracovat. Obvykle se jedná o první soubor v seznamu souborů kompilovat při zobrazení podle abecedy. Z tohoto důvodu je nejlepší určit soubor výstupu pomocí `/out` možnost.  
  
> [!NOTE]
>  `/recurse` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje všechny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory v aktuálním adresáři.  
  
```  
vbc *.vb  
```  
  
 Následující kód zkompiluje všechny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory `Test\ABC` adresář a všechny adresáře níže a poté generuje `Test.ABC.dll`.  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
