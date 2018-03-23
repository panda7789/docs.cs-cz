---
title: -win32icon
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95b2e2b4542f2e396a136f6a3d9baeb3e0c037a3
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-win32icon"></a>-win32icon
Vloží soubor .ico ve výstupním souboru. Tento soubor .ico, který představuje výstupní soubor v **Průzkumníka souborů**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`filename`|Soubor .ico, který chcete přidat do výstupního souboru. Uzavřete název souboru v uvozovkách ("") Pokud obsahuje mezeru.|  
  
## <a name="remarks"></a>Poznámky  
 Soubor .ico, který můžete vytvořit s Microsoft Windows prostředků kompilátoru (RC). Kompilátor prostředků je vyvolán při kompilaci Visual C++ program; soubor .ico, který je vytvořen ze souboru .rc. `-win32icon` a `-win32resource` možnosti se vzájemně vylučují.  
  
 Najdete v části [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) k odkazu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků, nebo [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků. V tématu [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res soubor naimportovat.  
  
|Chcete-li nastavit - win32icon v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **aplikace** kartě.<br />3.  Změňte hodnotu v **ikonu** pole.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a připojí soubor .ico `Rf.ico`.  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
