---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: bce2d98a8915e80cdecd7b67029b0c872cf70140
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-noconfig"></a>-noconfig
Určuje, že kompilátor nesmí odkazovat na automaticky běžně používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení nebo import `System` a `Microsoft.VisualBasic` obory názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 `-noconfig` Říká kompilátoru nechcete kompilovat s Vbc.rsp souboru, který se nachází ve stejném adresáři jako soubor Vbc.exe. Soubor Vbc.rsp odkazuje běžně používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení a importy `System` a `Microsoft.VisualBasic` obory názvů. Kompilátor implicitně odkazuje na sestavení System.dll, pokud `-nostdlib` je zadána možnost. `-nostdlib` Říká kompilátoru nechcete kompilovat s Vbc.rsp nebo automaticky odkazovat System.dll sestavení.  
  
> [!NOTE]
>  Sestavení Mscorlib.dll a souboru Microsoft.VisualBasic.dll jsou vždy odkazovat.  
  
 Můžete upravit soubor Vbc.rsp můžete určit další kompilátoru možnosti, které mají být zahrnuty v každé Vbc.exe kompilaci (s výjimkou při zadávání `-noconfig` možnost). Další informace najdete v tématu [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Kompilátor zpracovává možnosti předaný `vbc` poslední příkaz. Jakákoliv možnost, na příkazovém řádku proto přepíše nastavení stejné možnosti v souboru Vbc.rsp.  
  
> [!NOTE]
>  `-noconfig` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
