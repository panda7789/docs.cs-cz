---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: a612a68cffd927f3e360406cca6d9daae4f66c86
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775626"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Určuje název sestavení, jehož součástí bude tento modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Označení|Definice|  
|---|---|  
|`assembly_name`|Název sestavení, jehož součástí bude tento modul.|  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor zpracuje `-moduleassemblyname` možnost pouze v případě, `-target:module` že byla zadána možnost. Způsobí to, že kompilátor vytvoří modul. Modul vytvořený kompilátorem je platný pouze pro sestavení zadané s `-moduleassemblyname` možností. Pokud umístíte modul do jiného sestavení, dojde k chybám za běhu.  
  
 `-moduleassemblyname` Možnost je nutná pouze v případě, že jsou splněny následující podmínky:  
  
- Datový typ v modulu potřebuje přístup k `Friend` typu v odkazovaném sestavení.  
  
- Odkazované sestavení udělilo přístup přítel k sestavení, do kterého bude modul sestaven.  
  
 Další informace o vytváření modulu naleznete v tématu [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Další informace o Friend sestaveních naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).  
  
> [!NOTE]
> Tato `-moduleassemblyname` možnost není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také

- [Postupy: sestavení vícesouborového sestavení](../../../framework/app-domains/build-multifile-assembly.md)
- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Friend – sestavení](../../../standard/assembly/friend.md)
