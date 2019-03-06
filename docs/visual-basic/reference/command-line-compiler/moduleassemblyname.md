---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: a16dd616c8a38dea4bd1779e4feea779b3a18e2d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375295"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Určuje název sestavení, které bude tento modul součástí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`assembly_name`|Název sestavení, které bude tento modul součástí.|  
  
## <a name="remarks"></a>Poznámky  
 Procesy, které kompilátor `-moduleassemblyname` možnost pouze tehdy, pokud `-target:module` byla zadána možnost. To způsobí, že kompilátor vytvoří modul. Modul vytvořený kompilátorem je platná pouze pro sestavení zadaným `-moduleassemblyname` možnost. Pokud umístíte modulu v jiném sestavení, bude docházet k chybám za běhu.  
  
 `-moduleassemblyname` Možnost je vyžadována, pouze v případě, že jsou splněny následující:  
  
-   Datový typ v modulu potřebuje přístup k `Friend` typ v odkazovaném sestavení.  
  
-   Odkazované sestavení má udělen Přátelský přístup sestavení k sestavení, do kterého bude sestaven modul.  
  
 Další informace o vytváření modulu najdete v tématu [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Další informace o přátelských sestavení naleznete v tématu [přátelských sestavení](../../../standard/assembly/friend-assemblies.md).  
  
> [!NOTE]
>  `-moduleassemblyname` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici, pouze pokud kompilujete z příkazového řádku.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vytváření vícesouborového sestavení](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [– referenční dokumentace (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Přátelská sestavení](../../../standard/assembly/friend-assemblies.md)
