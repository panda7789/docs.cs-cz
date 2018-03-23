---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14361c01d13238db8f820b43889716e2528097f5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Způsobí, že kompilátor není odkazovat automaticky standardní knihovny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>Poznámky  
 `-nostdlib` Odebráno automatické odkaz na sestavení System.dll a zabrání čtení souboru Vbc.rsp kompilátoru. Vbc.rsp souboru, který se nachází ve stejném adresáři jako soubor Vbc.exe, odkazuje na běžně používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení a importy `System` a `Microsoft.VisualBasic` obory názvů.  
  
> [!NOTE]
>  Sestavení Mscorlib.dll a souboru Microsoft.VisualBasic.dll jsou vždy odkazovat.  
  
> [!NOTE]
>  `-nostdlib` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` bez odkazující na standardní knihovny. Je nutné nastavit `_MYTYPE` konstanty podmíněné kompilace řetězec "Prázdný" Odebrat `My` objektu.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Přizpůsobení výběru objektů dostupných v oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
