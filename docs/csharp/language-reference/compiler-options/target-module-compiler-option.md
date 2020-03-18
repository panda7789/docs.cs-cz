---
title: -target:modul (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602438"
---
# <a name="-targetmodule-c-compiler-options"></a>-target:modul (C# Možnosti kompilátoru)
Tato možnost způsobí, že kompilátor negeneruje manifest sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení bude mít výstupní soubor vytvořený kompilací s touto možností příponu .netmodule.  
  
 Soubor, který nemá manifest sestavení, nelze načíst běžným jazykem rozhraní .NET Framework. Takový soubor však může být začleněn do manifestu sestavení sestavení pomocí [-addmodule](./addmodule-compiler-option.md).  
  
 Pokud je v jedné kompilaci vytvořeno více než jeden modul, budou [interní](../keywords/internal.md) typy v jednom modulu k dispozici ostatním modulům v kompilaci. Když kód v jednom `internal` modulu odkazuje na typy v jiném modulu, pak musí být oba moduly začleněny do manifestu sestavení pomocí **-addmodule**.  
  
 Vytvoření modulu není podporováno ve vývojovém prostředí sady Visual Studio.  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` `in.netmodule`, vytváření :  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-target (Možnosti kompilátoru Jazyka C#)](./target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](./index.md)
