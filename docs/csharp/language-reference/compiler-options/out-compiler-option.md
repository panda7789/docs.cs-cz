---
title: -out (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: ea371dc968c8d8bf1569d17531cf7f6faff1d315
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210676"
---
# <a name="-out-c-compiler-options"></a>-out (možnosti kompilátoru C#)
**-Out** parametr určuje název výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název výstupní soubor vytvořený kompilátorem.  
  
## <a name="remarks"></a>Poznámky  
 Na příkazovém řádku je možné zadat víc výstupních souborů pro kompilaci. Kompilátor očekává, že jeden nebo více zdrojových souborů po **-out** možnost. Potom všechny soubory zdrojového kódu se zkompiluje do výstupní soubor určený parametrem, který **-out** možnost.  
  
 Zadejte úplný název a příponu souboru, který chcete vytvořit.  
  
 Pokud nezadáte název výstupního souboru:  
  
-   .Exe bude trvat, než jeho název souboru se zdrojovým kódem, který obsahuje **hlavní** metody.  
  
-   .Dll nebo .netmodule bude trvat, než jeho název prvního souboru se zdrojovým kódem.  
  
 Soubor zdrojového kódu používá ke kompilaci jeden výstupní soubor nelze použít ve stejné kompilaci pro kompilaci jiné výstupní soubor.  
  
 Při vytváření několika výstupních souborů do příkazového řádku kompilace, mějte na paměti, kterou lze pouze jednu z výstupních souborů sestavení a pouze první výstupní soubor zadaný (implicitně nebo explicitně s **-out**) může být sestavení .  
  
 Všechny moduly, které vytváří jako část kompilace stát soubory přidružené k žádné sestavení také vytvořit za kompilace. Použití [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) zobrazíte zobrazit přidružené soubory v manifestu sestavení.  
  
 -Out – možnost kompilátoru je nutná pro exe cíl sestavení typu friend. Další informace najdete v části [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **vlastnosti** stránky.  
  
2.  Klikněte na tlačítko **aplikace** stránku vlastností.  
  
3.  Upravit **název sestavení** vlastnost.  
  
     Programové nastavení tohoto parametru kompilátoru: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> je vlastnost jen pro čtení, což je určeno ke kombinaci komponent typu projektu (exe, knihovny a tak dále) a název sestavení. Úprava jeden nebo oba z těchto vlastností bude nutné nastavit název výstupního souboru.  
  
## <a name="example"></a>Příklad  
 Kompilace `t.cs` a vytvořit výstupní soubor `t.exe`, a také sestavení `t2.cs` a vytvoří výstupní soubor modulu `mymodule.netmodule`:  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Přátelská sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
