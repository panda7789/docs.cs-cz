---
title: "-addmodule (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2652102682de9dff24c66180dde36f33b4b6bbfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule-c-compiler-options"></a>/addmodule (Možnosti kompilátoru C#)
Tato možnost přidá modul, který byl vytvořen s přepínačem target: module do aktuální kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Arguments  
 `file`, `file2`  
 Výstupní soubor, který obsahuje metadata. Soubor nemůže obsahovat manifest sestavení. K importu více než jeden soubor, oddělte názvy souborů čárkou nebo středníkem.  
  
## <a name="remarks"></a>Poznámky  
 Všechny moduly přidané pomocí **/addmodule** musí být ve stejném adresáři jako výstupní soubor za běhu. To znamená můžete zadat modul v libovolného adresáře v době kompilace, ale modul musí být v adresáři aplikace za běhu. Pokud není modul v době běhu v adresáři aplikace, zobrazí se <xref:System.TypeLoadException>.  
  
 `file`nemůže obsahovat sestavení. Například pokud výstupní soubor byl vytvořen s [/target: Module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), jeho metadata můžete importovat pomocí **/addmodule**.  
  
 Pokud výstupní soubor byl vytvořen s **/target** možnost jiné než **/target: Module**, jeho metadata nelze importovat pomocí **/addmodule** , ale mohou být importována pomocí [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Tato možnost kompilátoru je k dispozici v sadě Visual Studio; Projekt nelze odkazovat na modul. Tato možnost kompilátoru navíc nelze změnit prostřednictvím kódu programu.  
  
## <a name="example"></a>Příklad  
 Kompilace zdrojového souboru `input.cs` a přidat metadata z `metad1.netmodule` a `metad2.netmodule` k vytvoření `out.exe`:  
  
```console  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
 [Vícesouborová sestavení](../../../framework/app-domains/multifile-assemblies.md)  
 [Postupy: vytváření vícesouborového sestavení](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
