---
title: /nostdlib (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9d76563a5b3d439495899e07ce2df59c0acd75e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nostdlib-visual-basic"></a>/nostdlib (Visual Basic)
Způsobí, že kompilátor není odkazovat automaticky standardní knihovny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/nostdlib  
```  
  
## <a name="remarks"></a>Poznámky  
 `/nostdlib` Odebráno automatické odkaz na sestavení System.dll a zabrání čtení souboru Vbc.rsp kompilátoru. Soubor Vbc.rsp – který se nachází ve stejném adresáři jako soubor Vbc.exe – odkazuje běžně používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení a importy `System` a `Microsoft.VisualBasic` obory názvů.  
  
> [!NOTE]
>  Sestavení Mscorlib.dll a souboru Microsoft.VisualBasic.dll jsou vždy odkazovat.  
  
> [!NOTE]
>  `/nostdlib` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` bez odkazující na standardní knihovny. Je nutné nastavit `_MYTYPE` konstanty podmíněné kompilace řetězec "Prázdný" Odebrat `My` objektu.  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [/ noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Přizpůsobení výběru objektů jsou k dispozici v mé](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
