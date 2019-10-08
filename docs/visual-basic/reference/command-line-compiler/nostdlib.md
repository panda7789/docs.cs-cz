---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 819505df2e7d5f93302f9ed601de856e36ed7124
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005411"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Způsobí, že kompilátor nebude automaticky odkazovat na standardní knihovny.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-nostdlib` odstraní automatický odkaz na sestavení System. dll a zabrání kompilátoru v čtení souboru Vbc. rsp. Soubor Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe, odkazuje na běžně používané .NET Framework sestavení a importuje obory názvů `System` a `Microsoft.VisualBasic`.  
  
> [!NOTE]
> Na sestavení knihovny mscorlib. dll a Microsoft. VisualBasic. dll jsou odkazy vždy odkazovány.  
  
> [!NOTE]
> Možnost `-nostdlib` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` bez odkazování na standardní knihovny. Chcete-li odebrat objekt `My`, je nutné nastavit konstantu podmíněné kompilace `_MYTYPE` na řetězec "Empty".  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Přizpůsobení výběru objektů dostupných v oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
