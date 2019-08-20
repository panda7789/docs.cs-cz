---
title: -target:module (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602438"
---
# <a name="-targetmodule-c-compiler-options"></a>-target:module (C# Compiler Options)
Tato možnost způsobí, že kompilátor negeneruje manifest sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení bude mít výstupní soubor vytvořený kompilací s touto možností rozšíření. netmodule.  
  
 Soubor, který nemá manifest sestavení, nelze načíst pomocí .NET Framework modulu CLR (Common Language Runtime). Takový soubor však lze začlenit do manifestu sestavení sestavení pomocí [addmodule –](./addmodule-compiler-option.md).  
  
 Je-li v jedné kompilaci vytvořen více než jeden modul, [interní](../keywords/internal.md) typy v jednom modulu budou k dispozici pro ostatní moduly v kompilaci. V případě, že kód v `internal` jednom modulu odkazuje na typy v jiném modulu, musí být oba moduly začleněny do manifestu sestavení, a to pomocí **-addmodule –** .  
  
 Vytvoření modulu není podporováno ve vývojovém prostředí sady Visual Studio.  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.ProjectProperties3.OutputType%2A>v tématu.  
  
## <a name="example"></a>Příklad  
 Kompilovat `in.cs`, vytvořit `in.netmodule`:  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [-Target (C# možnosti kompilátoru)](./target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](./index.md)
