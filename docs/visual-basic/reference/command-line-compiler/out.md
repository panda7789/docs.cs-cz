---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 6b005ac26e3fffad350cb4ce52f7757c9fff2ac1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005330"
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
Určuje název výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`filename`|Požadováno. Název výstupního souboru, který kompilátor vytvoří. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").|  
  
## <a name="remarks"></a>Poznámky  
 Zadejte úplný název a příponu souboru, který se má vytvořit. Pokud to neuděláte, soubor. exe převezme svůj název ze souboru zdrojového kódu obsahujícího postup `Sub Main` a soubor. dll převezme svůj název z prvního souboru zdrojového kódu.  
  
 Pokud zadáte název souboru bez přípony. exe nebo. dll, kompilátor pro vás automaticky přidá rozšíření v závislosti na hodnotě zadané pro možnost kompilátoru `-target`.  
  
|Nastavení v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **aplikace** .<br />3. upravte hodnotu v poli **název sestavení** .|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a vytvoří výstupní soubor `T2.exe`.  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
