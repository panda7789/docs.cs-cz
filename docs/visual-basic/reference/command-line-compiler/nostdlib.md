---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: db6b047f521d8ef44d2bd1b70b654a4233ebb1a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347915"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Způsobí, že kompilátor nebude automaticky odkazovat na standardní knihovny.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a>Poznámky  
 `-nostdlib` Možnost odebere automatický odkaz na sestavení System. dll a zabrání kompilátoru v čtení souboru Vbc. rsp. Soubor Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe, odkazuje na běžně používané .NET Framework sestavení a importuje obory názvů `System` a. `Microsoft.VisualBasic`  
  
> [!NOTE]
> Na sestavení knihovny mscorlib. dll a Microsoft. VisualBasic. dll jsou odkazy vždy odkazovány.  
  
> [!NOTE]
> Tato `-nostdlib` možnost není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` bez odkazování na standardní knihovny. Chcete-li odebrat `_MYTYPE` `My` objekt, je nutné nastavit konstantu podmíněné kompilace na řetězec "Empty".  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Viz také

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Přizpůsobení výběru objektů dostupných v oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
