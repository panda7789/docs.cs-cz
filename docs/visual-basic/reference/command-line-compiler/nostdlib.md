---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 1c3c70b24de5163ca004b41a21017205a19d9730
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583374"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Způsobí, že kompilátor, aby automaticky odkazovat na standardní knihovny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>Poznámky  
 `-nostdlib` Možnost odebere automatické odkaz na sestavení System.dll a zabrání čtení soubor Vbc.rsp kompilátoru. Soubor Vbc.rsp, který je umístěn ve stejném adresáři jako soubor Vbc.exe, odkazuje na běžně používané sestavení rozhraní .NET Framework a importuje `System` a `Microsoft.VisualBasic` obory názvů.  
  
> [!NOTE]
>  Vždy je odkazováno na sestavení Mscorlib.dll a Microsoft.VisualBasic.dll.  
  
> [!NOTE]
>  `-nostdlib` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` bez odkazování na standardní knihovny. Je nutné nastavit `_MYTYPE` – Konstanta podmíněné kompilace na řetězec "Prázdný" odeberte `My` objektu.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Přizpůsobení výběru objektů dostupných v oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
