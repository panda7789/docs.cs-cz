---
title: -win32res (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 3bb1614fcf28c62a9000c9b96af2f046f329fb1e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794374"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (možnosti kompilátoru C#)
Možnost **-win32res** vloží prostředek Win32 do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Soubor prostředků, který chcete přidat do výstupního souboru.  
  
## <a name="remarks"></a>Poznámky  
 Soubor prostředků Win32 se dá vytvořit s [kompilátorem prostředků](resource-compiler-option.md). Nástroj Resource Compiler je vyvolán při kompilaci programu Visual C++; soubor .res je vytvořen ze souboru .rc.  
  
 Prostředek Win32 může obsahovat informace o verzi nebo bitmapě (ikony), které vám pomůžou identifikovat vaši aplikaci v Průzkumníkovi souborů. Pokud nezadáte **-win32res**, kompilátor vygeneruje informace o verzi na základě verze sestavení.  
  
 Viz [– linkresource –](./linkresource-compiler-option.md) (odkazování) nebo [-Resource](./resource-compiler-option.md) (pro připojení) .NET Frameworkho souboru prostředků.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **aplikace** .  
  
3. Klikněte na tlačítko **soubor prostředků** a vyberte soubor pomocí pole se seznamem.  
  
## <a name="example"></a>Příklad  
 Zkompilujte `in.cs` a připojte soubor `rf.res` prostředků Win32 k vytvoření `in.exe`:  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
