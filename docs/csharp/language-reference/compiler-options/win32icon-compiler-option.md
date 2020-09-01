---
description: -win32icon (možnosti kompilátoru C#)
title: -win32icon (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 76a54f9011371492bdc15f15c3e40d51082deed3
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138407"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (možnosti kompilátoru C#)
Možnost **-win32icon** vloží soubor. ico do výstupního souboru, který poskytne výstupnímu souboru požadovaný vzhled v Průzkumníkovi souborů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Soubor. ico, který chcete přidat do výstupního souboru.  
  
## <a name="remarks"></a>Poznámky  
 Soubor. ico se dá vytvořit s [kompilátorem prostředků](/windows/desktop/menurc/resource-compiler). Kompilátor prostředků je vyvolán při kompilování Visual C++ programu; soubor. ico je vytvořen ze souboru. rc.  
  
 Viz [– linkresource –](./linkresource-compiler-option.md) (odkazování) nebo [-Resource](./resource-compiler-option.md) (pro připojení) .NET Frameworkho souboru prostředků. Viz [-win32res](./win32res-compiler-option.md) pro import souboru. res.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránky **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **aplikace** .  
  
3. Upravte vlastnost **ikona aplikace** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A> .  
  
## <a name="example"></a>Příklad  
 Zkompilujte `in.cs` a připojte soubor. ico `rf.ico` k výrobě `in.exe` :  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
