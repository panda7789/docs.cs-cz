---
description: '-target: winexe (možnosti kompilátoru C#)'
title: '-target: winexe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 8a1be07455b54b375106fef1fb480d7abd2f1ca4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124718"
---
# <a name="-targetwinexe-c-compiler-options"></a>-target: winexe (možnosti kompilátoru C#)
Možnost **-target: winexe** způsobí, že kompilátor vytvoří spustitelný soubor (exe), program systému Windows.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>Poznámky  
 Spustitelný soubor se vytvoří s příponou. exe. Program systému Windows je jeden, který poskytuje uživatelské rozhraní z knihovny .NET Framework nebo pomocí rozhraní API systému Windows.  
  
 Pro vytvoření konzolové aplikace použijte [příkaz-target: exe](./target-exe-compiler-option.md) .  
  
 Pokud není uvedeno jinak s možností [-out](./out-compiler-option.md) , název výstupního souboru převezme název vstupního souboru, který obsahuje metodu [Main](../../programming-guide/main-and-command-args/index.md) .  
  
 Je-li parametr zadán na příkazovém řádku, všechny soubory, dokud není použita možnost Next **-out** nebo [-target](./target-compiler-option.md) pro vytvoření programu systému Windows.  
  
 V souborech zdrojového kódu, které jsou zkompilovány do souboru. exe, je vyžadována jedna a pouze jedna metoda **Main** . Možnost [-Main](./main-compiler-option.md) umožňuje určit, která třída obsahuje metodu **Main** , v případech, kdy váš kód má více než jednu třídu s metodou **Main** .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **aplikace** .  
  
3. Upravte vlastnost **Typ výstupu** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .  
  
## <a name="example"></a>Příklad  
 Kompilovat `in.cs` do programu systému Windows:  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-Target (možnosti kompilátoru C#)](./target-compiler-option.md)
- [Možnosti kompilátoru C#](./index.md)
