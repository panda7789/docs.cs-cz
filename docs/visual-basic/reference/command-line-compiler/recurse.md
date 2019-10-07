---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 71613af0f1c319801296180d49dbacfedf0ceca4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005262"
---
# <a name="-recurse"></a>-recurse
Zkompiluje soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře, nebo adresáře projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 Volitelné. Adresář, ve kterém chcete zahájit hledání. Pokud není zadán, hledání začne v adresáři projektu.  
  
 `file`  
 Požadováno. Soubory, které chcete vyhledat. Zástupné znaky jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít zástupné znaky v názvu souboru k zkompilování všech vyhovujících souborů v adresáři projektu bez použití `-recurse`. Pokud není zadán žádný název výstupního souboru, kompilátor vyloží název výstupního souboru v prvním zpracovávaném vstupním souboru. Většinou se jedná o první soubor v seznamu souborů kompilovaných při abecedním zobrazení. Z tohoto důvodu je nejlepší zadat výstupní soubor pomocí možnosti `-out`.  
  
> [!NOTE]
> Možnost `-recurse` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje všechny Visual Basic soubory v aktuálním adresáři.  
  
```console
vbc *.vb  
```  
  
 Následující příkaz zkompiluje všechny Visual Basic soubory v adresáři `Test\ABC` a všech adresářích pod ním a pak vygeneruje `Test.ABC.dll`.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
