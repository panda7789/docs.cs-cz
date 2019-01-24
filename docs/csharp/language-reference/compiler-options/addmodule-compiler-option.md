---
title: -addmodule (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: f45afd277818d7e1658751f2aae0b2153c940eee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617509"
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule (možnosti kompilátoru C#)
Tato možnost přidá modul, který byl vytvořen s přepínačem target: module aktuální kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Arguments  
 `file`, `file2`  
 Výstupní soubor obsahující metadata. Soubor nesmí obsahovat manifest sestavení. Pokud chcete importovat více než jeden soubor, oddělte názvy souborů čárkami nebo středníkem.  
  
## <a name="remarks"></a>Poznámky  
 Všechny moduly přidané pomocí **- addmodule** musí být ve stejném adresáři jako výstupní soubor v době běhu. To znamená modul můžete zadat do libovolného adresáře v době kompilace, ale modul musí být v adresáři aplikace v době běhu. Pokud modul není v adresáři aplikace za běhu, zobrazí se <xref:System.TypeLoadException>.  
  
 `file` nemůže obsahovat sestavení. Například, pokud je výstupní soubor byl vytvořen s [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), jeho metadata, můžete je importovat s **- addmodule**.  
  
 Pokud výstupní soubor byl vytvořen pomocí **– cíl** možností jiných než **-target: module**, její metadata nelze je importovat s **- addmodule** ale můžete je importovat s [– referenční dokumentace](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Není k dispozici v sadě Visual Studio; toto – možnost kompilátoru Projekt nemůže odkazovat na modul. Tato možnost kompilátoru kromě toho nelze změnit prostřednictvím kódu programu.  
  
## <a name="example"></a>Příklad  
 Kompilaci zdrojového `input.cs` a přidá metadata z `metad1.netmodule` a `metad2.netmodule` k vytvoření `out.exe`:  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Vícesouborová sestavení](../../../framework/app-domains/multifile-assemblies.md)
- [Postupy: Vytváření vícesouborového sestavení](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
