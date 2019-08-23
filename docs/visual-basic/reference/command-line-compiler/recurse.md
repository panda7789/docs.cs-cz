---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 4281c7bf5a7972d323e1e649aaef437c7ee901ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956268"
---
# <a name="-recurse"></a>-recurse
Zkompiluje soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře, nebo adresáře projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 Volitelný parametr. Adresář, ve kterém chcete zahájit hledání. Pokud není zadán, hledání začne v adresáři projektu.  
  
 `file`  
 Povinný parametr. Soubory, které chcete vyhledat. Zástupné znaky jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít zástupné znaky v názvu souboru k zkompilování všech vyhovujících souborů v adresáři projektu bez `-recurse`použití. Pokud není zadán žádný název výstupního souboru, kompilátor vyloží název výstupního souboru v prvním zpracovávaném vstupním souboru. Většinou se jedná o první soubor v seznamu souborů kompilovaných při abecedním zobrazení. Z tohoto důvodu je nejlepší zadat výstupní soubor pomocí `-out` možnosti.  
  
> [!NOTE]
> Tato `-recurse` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje všechny Visual Basic soubory v aktuálním adresáři.  
  
```console
vbc *.vb  
```  
  
 Následující příkaz zkompiluje všechny Visual Basic soubory v `Test\ABC` adresáři a všech adresářích pod ním a pak vygeneruje. `Test.ABC.dll`  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
