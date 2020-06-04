---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 99f2b9d65f3c2a128e026666c5efb384e22643f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403145"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Určuje název sestavení, jehož součástí bude tento modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|`assembly_name`|Název sestavení, jehož součástí bude tento modul.|  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor zpracuje `-moduleassemblyname` možnost pouze v případě, že byla `-target:module` zadána možnost. Způsobí to, že kompilátor vytvoří modul. Modul vytvořený kompilátorem je platný pouze pro sestavení zadané s `-moduleassemblyname` možností. Pokud umístíte modul do jiného sestavení, dojde k chybám za běhu.  
  
 `-moduleassemblyname`Možnost je nutná pouze v případě, že jsou splněny následující podmínky:  
  
- Datový typ v modulu potřebuje přístup k `Friend` typu v odkazovaném sestavení.  
  
- Odkazované sestavení udělilo přístup přítel k sestavení, do kterého bude modul sestaven.  
  
 Další informace o vytváření modulu naleznete v tématu [-target (Visual Basic)](target.md). Další informace o Friend sestaveních naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).  
  
> [!NOTE]
> Tato `-moduleassemblyname` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také

- [Postupy: sestavení vícesouborového sestavení](../../../framework/app-domains/build-multifile-assembly.md)
- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-Target (Visual Basic)](target.md)
- [-main](main.md)
- [-Reference (Visual Basic)](reference.md)
- [-addmodule](addmodule.md)
- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [Friend – sestavení](../../../standard/assembly/friend.md)
