---
title: -target:winmdobj (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 85ae9a3f5e9b038c0c56935ec5af2b9b09d19f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204495"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target:winmdobj (Možnosti kompilátoru Jazyka C#)
Pokud použijete možnost kompilátoru **-target:winmdobj,** kompilátor vytvoří zprostředkující soubor .winmdobj, který můžete převést na binární soubor prostředí Windows Runtime (.winmd). Soubor .winmd pak mohou být spotřebovány programy JavaScript a C++ kromě spravovaných jazykových programů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Poznámky  
 **Winmdobj** nastavení signály kompilátoru, že je vyžadován zprostředkující modul. V reakci na to Visual Studio zkompiluje knihovnu tříd C# jako soubor .winmdobj. Soubor .winmdobj pak může být <xref:Microsoft.Build.Tasks.WinMDExp> podáván prostřednictvím nástroje pro export k vytvoření souboru metadat systému Windows (.winmd). Soubor .winmd obsahuje kód z původní knihovny i metadata WinMD, která je používána javascriptem nebo c++ a prostředím Windows Runtime.  
  
 Výstup souboru, který je kompilován pomocí možnosti kompilátoru **-target:winmdobj,** je navržen tak, aby byl použit pouze jako vstup pro nástroj pro export WimMDExp; samotný soubor .winmdobj není přímo odkazován.  
  
 Pokud nepoužijete možnost [-out,](./out-compiler-option.md) název výstupního souboru převezme název prvního vstupního souboru. [Main](../../programming-guide/main-and-command-args/index.md) metoda není vyžadována.  
  
 Pokud zadáte možnost -target:winmdobj na příkazovém řádku, všechny soubory až do další **možnosti -out** nebo [-target:module](./target-module-compiler-option.md) se použijí k vytvoření programu systému Windows.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí sady Visual Studio pro aplikaci pro Windows Store  
  
1. V **Průzkumníku řešení**otevřete místní nabídku projektu a pak zvolte **Vlastnosti**.  
  
2. Zvolte kartu **Aplikace.**  
  
3. V seznamu **Typ výstupu** zvolte **Soubor WinMD**.  
  
     Možnost **Soubor WinMD** je dostupná jenom pro šablony aplikací pro Windows 8.x Store.  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Následující příkaz se `filename.cs` zkompiluje do zprostředkujícího souboru .winmdobj.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-target (Možnosti kompilátoru Jazyka C#)](./target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](./index.md)
