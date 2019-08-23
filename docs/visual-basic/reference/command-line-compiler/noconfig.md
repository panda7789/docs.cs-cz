---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ca184fa130d62dc118d0de551ac58f3165064029
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964397"
---
# <a name="-noconfig"></a>-noconfig
Určuje, že by kompilátor neměl automaticky odkazovat na běžně používaná .NET Framework sestavení nebo importovat `System` obory názvů a. `Microsoft.VisualBasic`  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 `-noconfig` Možnost instruuje kompilátor, že není zkompilován se souborem Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe. Soubor Vbc. rsp odkazuje na běžně používaná .NET Framework sestavení a importuje `System` obory názvů a. `Microsoft.VisualBasic` Kompilátor implicitně odkazuje na sestavení System. dll, pokud `-nostdlib` není zadána možnost. `-nostdlib` Možnost instruuje kompilátor, že není zkompilován s Vbc. rsp nebo automaticky odkazuje na sestavení System. dll.  
  
> [!NOTE]
> Na sestavení knihovny mscorlib. dll a Microsoft. VisualBasic. dll jsou odkazy vždy odkazovány.  
  
 Můžete upravit soubor Vbc. rsp a zadat další možnosti kompilátoru, které by měly být zahrnuty do každé kompilace Vbc. exe (kromě při určení `-noconfig` možnosti). Další informace naleznete v tématu [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Kompilátor zpracovává možnosti předané `vbc` příkazu jako poslední. Proto jakékoli možnosti na příkazovém řádku přepisuje nastavení stejné možnosti v souboru Vbc. rsp.  
  
> [!NOTE]
> Tato `-noconfig` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také:

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
