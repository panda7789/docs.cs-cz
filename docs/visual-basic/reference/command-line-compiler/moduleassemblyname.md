---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 479f9f639548eb81351d1df3f8f08b29b393cba1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890880"
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
  
 Další informace o vytváření modulu najdete v tématu [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Další informace o přátelských sestavení naleznete v tématu [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
> [!NOTE]
>  `-moduleassemblyname` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici, pouze pokud kompilujete z příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytváření vícesouborového sestavení](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [– referenční dokumentace (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Přátelská sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)
