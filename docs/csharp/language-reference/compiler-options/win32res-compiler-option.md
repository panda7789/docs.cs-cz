---
title: -win32res (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 39f02c4c2e060c4be40002a2f48b0da31004a9ae
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606194"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (C# možnosti kompilátoru)
Možnost **-win32res** vloží prostředek Win32 do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Soubor prostředků, který chcete přidat do výstupního souboru.  
  
## <a name="remarks"></a>Poznámky  
 Soubor prostředků Win32 se dá vytvořit s kompilátorem [prostředků](../../language-reference/compiler-options/resource-compiler-option.md). Nástroj Resource Compiler je vyvolán při kompilaci programu Visual C++; soubor .res je vytvořen ze souboru .rc.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
