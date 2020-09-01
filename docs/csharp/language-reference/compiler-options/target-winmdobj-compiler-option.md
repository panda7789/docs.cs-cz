---
description: '-target: winmdobj (možnosti kompilátoru C#)'
title: '-target: winmdobj (možnosti kompilátoru C#)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 66a4bddb34832705ad4779829e561afd9442be8f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139083"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target: winmdobj (možnosti kompilátoru C#)
Použijete-li možnost kompilátoru **-target: winmdobj** , kompilátor vytvoří zprostředkující soubor. winmdobj, který lze převést na soubor prostředí Windows Runtime binárního souboru (. winmd). Soubor. winmd pak může používat programy JavaScript a C++ kromě spravovaných jazykových programů.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Poznámky  
 Nastavení **winmdobj** signalizuje kompilátoru, že je vyžadován zprostředkující modul. V reakci Visual Studio zkompiluje knihovnu tříd C# jako soubor. winmdobj. Soubor. winmdobj lze následně dodávat prostřednictvím <xref:Microsoft.Build.Tasks.WinMDExp> Nástroje pro export a vytvořit tak soubor metadat Windows (. winmd). Soubor. winmd obsahuje kód z původní knihovny i metadata WinMD, která jsou používána v jazyce JavaScript nebo C++ a prostředí Windows Runtime.  
  
 Výstup souboru, který je zkompilován pomocí volby kompilátoru **-target: winmdobj** , je navržen tak, aby se pro nástroj pro export WimMDExp používal jenom jako vstup. na samotný soubor. winmdobj se neodkazuje přímo.  
  
 Pokud nepoužijete možnost [-out](./out-compiler-option.md) , název výstupního souboru vezme název prvního vstupního souboru. Metoda [Main](../../programming-guide/main-and-command-args/index.md) se nevyžaduje.  
  
 Zadáte-li možnost-target: winmdobj na příkazovém řádku, budou pro vytvoření programu systému Windows použity všechny soubory, dokud nebude použita možnost Další **-mimo** [cíl: modul](./target-module-compiler-option.md) .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí sady Visual Studio pro aplikaci pro Windows Store  
  
1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.  
  
2. Vyberte kartu **aplikace** .  
  
3. V seznamu **Typ výstupu** vyberte **soubor winmd**.  
  
     Možnost **soubor winmd** je k dispozici pouze pro šablony aplikací Windows 8. x Store.  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .  
  
## <a name="example"></a>Příklad  
 Následující příkaz se zkompiluje `filename.cs` do zprostředkujícího souboru. winmdobj.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-Target (možnosti kompilátoru C#)](./target-compiler-option.md)
- [Možnosti kompilátoru C#](./index.md)
