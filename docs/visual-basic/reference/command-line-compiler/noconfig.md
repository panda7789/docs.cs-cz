---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: c57ed1699d110959e9faf3dc3d43bcc200851c1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005443"
---
# <a name="-noconfig"></a>-noconfig
Určuje, že by kompilátor neměl automaticky odkazovat na běžně používaná .NET Framework sestavení nebo importovat `System` obory `Microsoft.VisualBasic` názvů a.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 `-noconfig` Možnost instruuje kompilátor, že není zkompilován se souborem Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe. Soubor Vbc. rsp odkazuje na běžně používaná .NET Framework sestavení a importuje obory `System` názvů `Microsoft.VisualBasic` a. Kompilátor implicitně odkazuje na sestavení System. dll, pokud není `-nostdlib` zadána možnost. `-nostdlib` Možnost instruuje kompilátor, že není zkompilován s Vbc. rsp nebo automaticky odkazuje na sestavení System. dll.  
  
> [!NOTE]
> Na sestavení knihovny mscorlib. dll a Microsoft. VisualBasic. dll jsou odkazy vždy odkazovány.  
  
 Můžete upravit soubor Vbc. rsp a zadat další možnosti kompilátoru, které by měly být zahrnuty do každé kompilace Vbc. exe (kromě při určení `-noconfig` možnosti). Další informace naleznete v tématu [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Kompilátor zpracovává možnosti předané `vbc` příkazu jako poslední. Proto jakékoli možnosti na příkazovém řádku přepisuje nastavení stejné možnosti v souboru Vbc. rsp.  
  
> [!NOTE]
> Tato `-noconfig` možnost není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
