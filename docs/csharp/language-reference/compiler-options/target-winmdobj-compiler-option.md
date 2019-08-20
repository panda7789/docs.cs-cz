---
title: '-target: winmdobj (C# možnosti kompilátoru)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: fe1332f9ed6de9c50c2509e29f22ed7c0e57ade9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606355"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target: winmdobj (C# možnosti kompilátoru)
Použijete-li možnost kompilátoru **-target: winmdobj** , kompilátor vytvoří zprostředkující soubor. winmdobj, který lze převést na soubor prostředí Windows Runtime binárního souboru (. winmd). Soubor. winmd lze následně spotřebovat pomocí jazyka JavaScript a C++ programů společně s spravovanými jazykovými programy.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Poznámky  
 Nastavení **winmdobj** signalizuje kompilátoru, že je vyžadován zprostředkující modul. V reakci aplikace Visual Studio zkompiluje knihovnu C# tříd jako soubor. winmdobj. Soubor. winmdobj lze následně dodávat prostřednictvím <xref:Microsoft.Build.Tasks.WinMDExp> nástroje pro export a vytvořit tak soubor metadat Windows (. winmd). Soubor. winmd obsahuje jak kód z původní knihovny, tak metadat WinMD, které používá JavaScript nebo C++ a prostředí Windows Runtime.  
  
 Výstup souboru, který je zkompilován pomocí volby kompilátoru **-target: winmdobj** , je navržen tak, aby se pro nástroj pro export WimMDExp používal jenom jako vstup. na samotný soubor. winmdobj se neodkazuje přímo.  
  
 Pokud nepoužijete možnost [-out](./out-compiler-option.md) , název výstupního souboru vezme název prvního vstupního souboru. Metoda [Main](../../programming-guide/main-and-command-args/index.md) se nevyžaduje.  
  
 Zadáte-li možnost-target: winmdobj na příkazovém řádku, budou pro vytvoření programu systému Windows použity všechny soubory, dokud nebude použita možnost Další **-mimo** [cíl: modul](./target-module-compiler-option.md) .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí sady Visual Studio pro aplikaci pro Windows Store  
  
1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.  
  
2. Vyberte kartu **aplikace** .  
  
3. V seznamu **Typ výstupu** vyberte **soubor winmd**.  
  
     Možnost **soubor winmd** je k dispozici pouze [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] pro šablony aplikace.  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.ProjectProperties3.OutputType%2A>v tématu.  
  
## <a name="example"></a>Příklad  
 Následující příkaz se zkompiluje `filename.cs` do zprostředkujícího souboru. winmdobj.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [-Target (C# možnosti kompilátoru)](./target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](./index.md)
