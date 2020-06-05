---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ee7cd1b8039a8d9312a8b058cc85c41ca536ed2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401937"
---
# <a name="-noconfig"></a>-noconfig
Určuje, že by kompilátor neměl automaticky odkazovat na běžně používaná .NET Framework sestavení nebo importovat `System` `Microsoft.VisualBasic` obory názvů a.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 `-noconfig`Možnost instruuje kompilátor, že není zkompilován se souborem Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe. Soubor Vbc. rsp odkazuje na běžně používaná .NET Framework sestavení a importuje `System` `Microsoft.VisualBasic` obory názvů a. Kompilátor implicitně odkazuje na sestavení System. dll, pokud `-nostdlib` není zadána možnost. `-nostdlib`Možnost instruuje kompilátor, že není zkompilován s Vbc. rsp nebo automaticky odkazuje na sestavení System. dll.  
  
> [!NOTE]
> Na sestavení knihovny mscorlib. dll a Microsoft. VisualBasic. dll jsou odkazy vždy odkazovány.  
  
 Můžete upravit soubor Vbc. rsp a zadat další možnosti kompilátoru, které by měly být zahrnuty do každé kompilace Vbc. exe (kromě při určení `-noconfig` Možnosti). Další informace naleznete v tématu [@ (určení souboru odezvy)](specify-response-file.md).  
  
 Kompilátor zpracovává možnosti předané `vbc` příkazu jako poslední. Proto jakékoli možnosti na příkazovém řádku přepisuje nastavení stejné možnosti v souboru Vbc. rsp.  
  
> [!NOTE]
> Tato `-noconfig` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také

- [-nostdlib (Visual Basic)](nostdlib.md)
- [Visual Basic Kompilátor příkazového řádku](index.md)
- [@ (určení souboru odezvy)](specify-response-file.md)
- [-Reference (Visual Basic)](reference.md)
