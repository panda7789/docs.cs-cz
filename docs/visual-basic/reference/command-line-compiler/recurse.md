---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 2fe1834c3e92c3eff016ffd7857a0473eb2e8b3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816418"
---
# <a name="-recurse"></a>-recurse
Zkompiluje soubory zdrojového kódu ve všech adresářích podřízené zadaný adresář nebo adresář projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 Volitelné. Adresář, ve kterém chcete, aby hledání začalo. Pokud není zadán, hledání začne v adresáři projektu.  
  
 `file`  
 Povinný parametr. Soubory, které chcete vyhledat. Zástupné znaky jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 Zástupné znaky v názvu souboru můžete použít ke kompilaci všech odpovídajících souborů v adresáři projektu bez použití `-recurse`. Pokud není zadán žádný název výstupního souboru, kompilátor odvodí název výstupního souboru na první zpracování vstupního souboru. Obvykle se jedná v prvním souboru v seznamu soubory zkompilovány při zobrazení podle abecedy. Z tohoto důvodu je nejvhodnější k určení souboru výstupu pomocí `-out` možnost.  
  
> [!NOTE]
>  `-recurse` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje všechny soubory jazyka Visual Basic v aktuálním adresáři.  
  
```console
vbc *.vb  
```  
  
 Následující příkaz zkompiluje všechny soubory jazyka Visual Basic v `Test\ABC` adresář a všechny adresáře pod něj a poté vygeneruje `Test.ABC.dll`.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
