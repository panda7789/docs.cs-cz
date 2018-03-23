---
title: -out (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cc3779f9efda8cf48107a7c16e31f8ff05a456d
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
Určuje název souboru výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`filename`|Požadováno. Název výstupního souboru kompilátoru vytvoří. Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách ("").|  
  
## <a name="remarks"></a>Poznámky  
 Zadejte úplný název a příponu souboru pro vytvoření. Pokud ho použít nechcete, soubor .exe trvá její název ze zdrojového kódu soubor obsahující `Sub Main` postupu a soubor .dll vezme její název ze první soubor zdrojového kódu.  
  
 Pokud zadáte název souboru bez přípony .exe nebo .dll, kompilátor automaticky přidá rozšíření, v závislosti na zadaná hodnota parametru `-target` – možnost kompilátoru.  
  
|Chcete-li nastavit - odhlašování v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **aplikace** kartě.<br />3.  Změňte hodnotu v **název sestavení** pole.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a vytvoří výstupní soubor `T2.exe`.  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
