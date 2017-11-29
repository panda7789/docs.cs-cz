---
title: /noconfig
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94d13ccf0168027f4560b980c41e2a001ff503fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="noconfig"></a>/noconfig
Určuje, že kompilátor nesmí odkazovat na automaticky běžně používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení nebo import `System` a `Microsoft.VisualBasic` obory názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 `/noconfig` Říká kompilátoru nechcete kompilovat s Vbc.rsp souboru, který se nachází ve stejném adresáři jako soubor Vbc.exe. Soubor Vbc.rsp odkazuje běžně používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení a importy `System` a `Microsoft.VisualBasic` obory názvů. Kompilátor implicitně odkazuje na sestavení System.dll, pokud `/nostdlib` je zadána možnost. `/nostdlib` Říká kompilátoru nechcete kompilovat s Vbc.rsp nebo automaticky odkazovat System.dll sestavení.  
  
> [!NOTE]
>  Sestavení Mscorlib.dll a souboru Microsoft.VisualBasic.dll jsou vždy odkazovat.  
  
 Můžete upravit soubor Vbc.rsp můžete určit další kompilátoru možnosti, které mají být zahrnuty v každé Vbc.exe kompilaci (s výjimkou při zadávání `/noconfig` možnost). Další informace najdete v tématu [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Kompilátor zpracovává možnosti předaný `vbc` poslední příkaz. Jakákoliv možnost, na příkazovém řádku proto přepíše nastavení stejné možnosti v souboru Vbc.rsp.  
  
> [!NOTE]
>  `/noconfig` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [/ nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [@ (Určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [/ Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
