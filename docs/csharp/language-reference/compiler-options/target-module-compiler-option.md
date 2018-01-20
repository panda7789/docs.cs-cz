---
title: "-target: module (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 679d659b2806fb875f908cee840a62278c99096f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-targetmodule-c-compiler-options"></a>-target: module (možnosti kompilátoru C#)
Tato možnost způsobí, že kompilátor není generování manifestu sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení bude mít vytvořené kompilace pomocí této možnosti výstupního souboru rozšíření .netmodule.  
  
 Soubor, který nemá manifest sestavení nelze načíst pomocí modulu CLR rozhraní .NET Framework. Však takový soubor může být součástí manifestu sestavení pomocí [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Pokud je vytvořen více než jeden modul v jedné kompilaci [interní](../../../csharp/language-reference/keywords/internal.md) typy v jeden modul bude k dispozici pro jiné moduly v kompilace. Pokud kód odkazuje jeden modul `internal` typy v jiný modul, pak oba moduly musí být začleněny do manifestu sestavení pomocí **- addmodule**.  
  
 Vytvoření modulu není podporováno ve vývojovém prostředí sady Visual Studio.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs`, vytváření `in.netmodule`:  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
