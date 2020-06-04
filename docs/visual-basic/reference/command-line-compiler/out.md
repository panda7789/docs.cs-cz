---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 75f3ee7f24112f911803732ccb8d39eeafa95e3d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400510"
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
Určuje název výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|`filename`|Povinná hodnota. Název výstupního souboru, který kompilátor vytvoří. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").|  
  
## <a name="remarks"></a>Poznámky  
 Zadejte úplný název a příponu souboru, který se má vytvořit. Pokud to neuděláte, soubor. exe převezme svůj název ze souboru zdrojového kódu, který obsahuje `Sub Main` proceduru, a soubor. dll převezme svůj název z prvního souboru zdrojového kódu.  
  
 Pokud zadáte název souboru bez přípony. exe nebo. dll, kompilátor pro vás automaticky přidá rozšíření v závislosti na hodnotě zadané pro `-target` možnost kompilátoru.  
  
|Nastavení v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **aplikace** .<br />3. upravte hodnotu v poli **název sestavení** .|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a vytvoří výstupní soubor `T2.exe` .  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-Target (Visual Basic)](target.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
