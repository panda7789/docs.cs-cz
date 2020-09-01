---
description: '-target: Module (možnosti kompilátoru C#)'
title: '-target: Module (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 2c592d2fe001bb0908a06a6eb3287a39040b8715
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128449"
---
# <a name="-targetmodule-c-compiler-options"></a>-target: Module (možnosti kompilátoru C#)
Tato možnost způsobí, že kompilátor negeneruje manifest sestavení.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení bude mít výstupní soubor vytvořený kompilací s touto možností rozšíření. netmodule.  
  
 Soubor, který nemá manifest sestavení, nelze načíst pomocí .NET Framework modulu CLR (Common Language Runtime). Takový soubor však lze začlenit do manifestu sestavení sestavení pomocí [addmodule –](./addmodule-compiler-option.md).  
  
 Je-li v jedné kompilaci vytvořen více než jeden modul, [interní](../keywords/internal.md) typy v jednom modulu budou k dispozici pro ostatní moduly v kompilaci. V případě, že kód v jednom modulu odkazuje na `internal` typy v jiném modulu, musí být oba moduly začleněny do manifestu sestavení, a to pomocí **-addmodule –**.  
  
 Vytvoření modulu není podporováno ve vývojovém prostředí sady Visual Studio.  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .  
  
## <a name="example"></a>Příklad  
 Kompilovat `in.cs` , vytvořit `in.netmodule` :  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-Target (možnosti kompilátoru C#)](./target-compiler-option.md)
- [Možnosti kompilátoru C#](./index.md)
