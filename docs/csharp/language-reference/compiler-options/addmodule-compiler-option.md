---
title: -addmodule (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 148a63c37cfbc4c60448adccde10947e91e22bb9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970176"
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule (Možnosti kompilátoru Jazyka C#)
Tato možnost přidá modul, který byl vytvořen s přepínačem target:module do aktuální kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`, `file2`  
 Výstupní soubor, který obsahuje metadata. Soubor nemůže obsahovat manifest sestavení. Chcete-li importovat více než jeden soubor, oddělte názvy souborů čárkou nebo středníkem.  
  
## <a name="remarks"></a>Poznámky  
 Všechny moduly přidané s **-addmodule** musí být ve stejném adresáři jako výstupní soubor za běhu. To znamená, že můžete zadat modul v libovolném adresáři v době kompilace, ale modul musí být v adresáři aplikace za běhu. Pokud modul není v adresáři aplikace za běhu, <xref:System.TypeLoadException>získáte .  
  
 `file`nemůže obsahovat sestavení. Například pokud výstupní soubor byl vytvořen s [-target:module](./target-module-compiler-option.md), jeho metadata lze importovat s **-addmodule**.  
  
 Pokud byl výstupní soubor vytvořen s jinou volbou **-target** než **-target:module**, jeho metadata nelze importovat pomocí **modulu -addmodule,** ale lze jej importovat pomocí [-reference](./reference-compiler-option.md).  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio; projekt nemůže odkazovat na modul. Kromě toho tuto možnost kompilátoru nelze změnit programově.  
  
## <a name="example"></a>Příklad  
 Kompilujte `input.cs` zdrojový soubor `metad1.netmodule` a `metad2.netmodule` přidejte metadata z a k vytvoření `out.exe`:  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Vícesouborová sestavení](../../../framework/app-domains/multifile-assemblies.md)
- [Postupy: Vytváření vícesouborového sestavení](../../../framework/app-domains/build-multifile-assembly.md)
