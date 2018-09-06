---
title: '-target: module (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 7cc0e48a7a4a3ec3f28c89e80fadf6aa7e1130f2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865059"
---
# <a name="-targetmodule-c-compiler-options"></a>-target: module (možnosti kompilátoru C#)
Tato možnost způsobí, že kompilátor nevygeneruje manifest sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení bude mít výstupní soubor vytvořil kompilaci s touto možností rozšíření .netmodule.  
  
 Soubor, který nemá manifest sestavení nelze načíst pomocí rozhraní .NET Framework common language runtime. Však takový soubor může být součástí sestavení manifestu sestavení prostřednictvím [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Pokud se v jedné kompilace vytvoří více než jeden modul [interní](../../../csharp/language-reference/keywords/internal.md) typy v jeden modul bude k dispozici pro ostatní moduly v sestavení. Pokud kód v odkazech na jeden modul `internal` typy v jiném modulu, pak oba moduly musí být začleněny do manifestu sestavení pomocí **- addmodule**.  
  
 Vytvoření modulu není podporováno ve vývojovém prostředí sady Visual Studio.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs`, vytváření `in.netmodule`:  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Viz také  

- [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
