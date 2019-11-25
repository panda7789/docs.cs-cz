---
title: -target:winmdobj (C# Compiler Options)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 85ae9a3f5e9b038c0c56935ec5af2b9b09d19f20
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204495"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target:winmdobj (C# Compiler Options)
If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file. The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Poznámky  
 The **winmdobj** setting signals to the compiler that an intermediate module is required. In response, Visual Studio compiles the C# class library as a .winmdobj file. The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file. The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.  
  
 The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.  
  
 Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file. A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.  
  
 If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí sady Visual Studio pro aplikaci pro Windows Store  
  
1. In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.  
  
2. Choose the **Application** tab.  
  
3. In the **Output type** list, choose **WinMD File**.  
  
     The **WinMD File** option is available only for Windows 8.x Store app templates.  
  
 For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 The following command compiles `filename.cs` into an intermediate .winmdobj file.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [-target (C# Compiler Options)](./target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](./index.md)
