---
description: '-target: exe (možnosti kompilátoru C#)'
title: '-target: exe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 3cea52fe872fcb407206ee2063b93dc81447a3b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128501"
---
# <a name="-targetexe-c-compiler-options"></a>-target: exe (možnosti kompilátoru C#)
Možnost **-target: exe** způsobí, že kompilátor vytvoří spustitelný soubor (exe), konzolovou aplikaci.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-target: exe** je ve výchozím nastavení platná. Spustitelný soubor se vytvoří s příponou. exe.  
  
 Použití [-target: winexe](./target-winexe-compiler-option.md) k vytvoření spustitelného souboru programu systému Windows.  
  
 Pokud není uvedeno jinak s možností [-out](./out-compiler-option.md) , název výstupního souboru převezme název vstupního souboru, který obsahuje metodu [Main](../../programming-guide/main-and-command-args/index.md) .  
  
 Při zadání na příkazovém řádku se pro vytvoření souboru. exe použijí všechny soubory až **na další nebo** na **cíl: možnost modul** .  
  
 V souborech zdrojového kódu, které jsou zkompilovány do souboru. exe, je vyžadována jedna a pouze jedna metoda **Main** . Možnost [-Main](./main-compiler-option.md) kompilátoru umožňuje určit, která třída obsahuje metodu **Main** , v případech, kdy váš kód má více než jednu třídu s metodou **Main** .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **aplikace** .  
  
3. Upravte vlastnost **Typ výstupu** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .  
  
## <a name="example"></a>Příklad  
 Každý z následujících příkazových řádků bude zkompilován `in.cs` , vytváření `in.exe` :  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-Target (možnosti kompilátoru C#)](./target-compiler-option.md)
- [Možnosti kompilátoru C#](./index.md)
