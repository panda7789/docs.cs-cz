---
title: -target:winmdobj (C# Compiler Options)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 9cc85bf582d737114bc0e621a9568bbb9acb791b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319297"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target:winmdobj (C# Compiler Options)
Pokud používáte **-target: winmdobj** – možnost kompilátoru, kompilátor vytvoří přechodný soubor .winmdobj, který lze převést do binárního souboru (.winmd) souboru Windows Runtime. Soubor .winmd může být potom používán programy JavaScript a C++, kromě programů spravovaného jazyka.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Poznámky  
 **Winmdobj** nastavení signály na kompilátoru, že přechodný modul je vyžadován. V reakci Visual Studio zkompiluje knihovnu tříd C# jako soubor .winmdobj. Soubor .winmdobj pak lze vkládat až <xref:Microsoft.Build.Tasks.WinMDExp> exportovat nástroj k vytvoření souboru Windows metadata (.winmd). Soubor .winmd obsahuje kód z původní knihovny i metadata WinMD, který se používá jazyk JavaScript nebo C++ a modulem Windows Runtime.  
  
 Výstupní soubor, který je zkompilován s použitím **-target: winmdobj** – možnost kompilátoru je určen k použití pouze jako vstup pro nástroj pro export WimMDExp; samotný soubor .winmdobj není přímo odkazován.  
  
 Pokud nechcete použít [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá názvu prvního vstupního souboru. A [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda není vyžadována.  
  
 Pokud zadáte možnost / target: winmdobj na příkazovém řádku, všechny soubory až do další **-out** nebo [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) slouží k vytvoření programu Windows.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí sady Visual Studio pro aplikaci pro Windows Store  
  
1. V **Průzkumníka řešení**, otevřete místní nabídku pro váš projekt a klikněte na tlačítko **vlastnosti**.  
  
2. Zvolte **aplikace** kartu.  
  
3. V **typ výstupu** klikněte na položku **soubor WinMD**.  
  
     **Soubor WinMD** možnost je dostupná jenom pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] šablony aplikací.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz kompiluje `filename.cs` do přechodného souboru .winmdobj.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
