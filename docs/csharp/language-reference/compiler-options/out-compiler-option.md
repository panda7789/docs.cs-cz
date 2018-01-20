---
title: "-out (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8ca85293086f8747cc4aaff02e7d9b5628b1e88a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-out-c-compiler-options"></a>-out (možnosti kompilátoru C#)
**-Out** možnost určuje název souboru výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název výstupního souboru vytvořené kompilátoru.  
  
## <a name="remarks"></a>Poznámky  
 Na příkazovém řádku je možné zadat více výstupní soubory pro kompilaci. Kompilátor očekává, že jeden nebo více zdrojových souborů následující **-out** možnost. Potom všechny soubory zdrojového kódu se zkompiluje do výstupního souboru, který určeného **-out** možnost.  
  
 Zadejte úplný název a příponu souboru, který chcete vytvořit.  
  
 Pokud nezadáte název výstupního souboru:  
  
-   .exe bude trvat její název ze zdrojového souboru kódu, který obsahuje **hlavní** metoda.  
  
-   .Dll nebo .netmodule převezme název z první souboru se zdrojovým kódem.  
  
 Soubor zdrojového kódu použít zkompilovat jednu výstupní soubor nelze použít ve stejné kompilaci pro kompilaci jiného výstupního souboru.  
  
 Při vytváření více výstupních souborů v kompilaci příkazového řádku, mějte na paměti, že pouze jeden výstupních souborů může být sestavení a pouze první výstupní soubor zadaný (implicitně nebo explicitně s **-out**) může být sestavení .  
  
 Všechny moduly, vytvořené jako součást kompilace stát soubory přidružené k žádné sestavení také vytvořené ve kompilaci. Použití [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) zobrazíte manifest sestavení zobrazíte přidružené soubory.  
  
 -Out – možnost kompilátoru je nutná pro exe jako cíl přátelského sestavení. Další informace najdete v části [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **aplikace** stránku vlastností.  
  
3.  Změnit **název sestavení** vlastnost.  
  
     Nastavení této možnosti kompilátoru programu: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> je jen pro čtení vlastnost, která je určena kombinací typu projektu (exe, knihovny a tak dále) a název sestavení. Úprava jednoho nebo obou těchto vlastností bude nutné nastavit název výstupního souboru.  
  
## <a name="example"></a>Příklad  
 Kompilace `t.cs` a vytvoření výstupního souboru `t.exe`, a také sestavení `t2.cs` a vytvoření výstupního souboru modulu `mymodule.netmodule`:  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Přátelská sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
