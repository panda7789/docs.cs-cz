---
title: -win32icon (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606277"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (C# možnosti kompilátoru)
Možnost **-win32icon** vloží soubor. ico do výstupního souboru, který poskytne výstupnímu souboru požadovaný vzhled v Průzkumníkovi souborů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Soubor. ico, který chcete přidat do výstupního souboru.  
  
## <a name="remarks"></a>Poznámky  
 Soubor. ico se dá vytvořit s kompilátorem [prostředků](/windows/desktop/menurc/resource-compiler). Kompilátor prostředků je vyvolán při kompilování vizuálního C++ programu; soubor. ico je vytvořen ze souboru. rc.  
  
 Viz [– linkresource –](./linkresource-compiler-option.md) (odkazování) nebo [-Resource](./resource-compiler-option.md) (pro připojení) .NET Frameworkho souboru prostředků. Viz [-win32res](./win32res-compiler-option.md) pro import souboru. res.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránky **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **aplikace** .  
  
3. Upravte vlastnost **ikona aplikace** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>v tématu.  
  
## <a name="example"></a>Příklad  
 Zkompilujte `in.cs` a připojte soubor `rf.ico` . ico k výrobě `in.exe`:  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
