---
title: -win32icon (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606277"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (Možnosti kompilátoru Jazyka C#)
Volba **-win32icon** vloží do výstupního souboru soubor .ico, který dává výstupnímu souboru požadovaný vzhled v Průzkumníku souborů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Soubor ICO, který chcete přidat do výstupního souboru.  
  
## <a name="remarks"></a>Poznámky  
 Soubor .ico lze vytvořit pomocí [kompilátoru prostředků](/windows/desktop/menurc/resource-compiler). Kompilátor prostředků je vyvolán při kompilaci programu Visual C++; Soubor .ico je vytvořen ze souboru RC.  
  
 Viz [-linkresource](./linkresource-compiler-option.md) (odkaz) nebo [-resource](./resource-compiler-option.md) (připojit) soubor prostředků rozhraní .NET Framework. Viz [-win32res](./win32res-compiler-option.md) pro import souboru .res.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránky **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Aplikace.**  
  
3. Upravte vlastnost **ikony Aplikace.**  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` a připojení souboru `rf.ico` `in.exe`.ico k vytvoření :  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
