---
title: -addmodule – (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 148a63c37cfbc4c60448adccde10947e91e22bb9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970176"
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule – (C# možnosti kompilátoru)
Tato možnost přidá modul, který byl vytvořen s možností cíl: modul přepnutí na aktuální kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Arguments  
 `file`, `file2`  
 Výstupní soubor, který obsahuje metadata. Soubor nemůže obsahovat manifest sestavení. Chcete-li importovat více než jeden soubor, oddělte názvy souborů čárkou nebo středníkem.  
  
## <a name="remarks"></a>Poznámky  
 Všechny moduly přidané pomocí **-addmodule –** musí být ve stejném adresáři jako výstupní soubor v době běhu. To znamená, že můžete určit modul v jakémkoli adresáři v době kompilace, ale modul musí být v adresáři aplikace v době běhu. Pokud modul není v adresáři aplikace v době běhu, <xref:System.TypeLoadException>zobrazí se.  
  
 `file`nemůže obsahovat sestavení. Například pokud byl výstupní soubor vytvořen pomocí [-target: Module](./target-module-compiler-option.md), jeho metadata lze importovat pomocí **-addmodule –** .  
  
 Pokud byl výstupní soubor vytvořen s možností **-target** jinou než **-target: Module**, jeho metadata nelze importovat pomocí **-addmodule –** , ale lze je importovat s [odkazem](./reference-compiler-option.md).  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici; projekt nemůže odkazovat na modul. Tuto možnost kompilátoru nelze navíc změnit programově.  
  
## <a name="example"></a>Příklad  
 Zkompilujte zdrojový soubor `input.cs` a přidejte metadata z `metad1.netmodule` a `metad2.netmodule` do sestavení `out.exe`:  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Vícesouborová sestavení](../../../framework/app-domains/multifile-assemblies.md)
- [Postupy: Sestavení vícesouborového sestavení](../../../framework/app-domains/build-multifile-assembly.md)
