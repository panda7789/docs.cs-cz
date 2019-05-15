---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: dc48a8f79aa04892c514917da00b8fd6489695b1
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593082"
---
# <a name="-win32icon"></a>-win32icon
Vloží soubor .ico do výstupního souboru. Tento soubor .ico, který představuje výstupní soubor v **Průzkumníka souborů**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`filename`|Soubor .ico, který chcete přidat do výstupního souboru. Název souboru uzavřete do uvozovek ("") Pokud obsahuje mezery.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete vytvořit soubor .ico s Microsoft Windows Resource kompilátor (RC). Nástroj resource compiler je vyvolán při kompilaci programu v jazyce Visual C++; soubor .ico je vytvořen ze souboru .rc. `-win32icon` a `-win32resource` možnosti se vzájemně vylučují.  
  
 Zobrazit [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) k odkázání na soubor prostředků rozhraní .NET Framework nebo [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit soubor prostředků rozhraní .NET Framework. Zobrazit [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) importovat soubor .res.  
  
|Chcete-li nastavit - win32icon v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte na tlačítko **aplikace** kartu.<br />3.  Upravte hodnotu v **ikonu** pole.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a připojí soubor .ico `Rf.ico`.  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
