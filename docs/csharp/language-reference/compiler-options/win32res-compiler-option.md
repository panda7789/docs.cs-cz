---
title: -win32res (Možnosti kompilátoru Jazyka C#)
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606194"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (Možnosti kompilátoru Jazyka C#)
Možnost **-win32res** vloží prostředek Win32 do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Soubor prostředků, který chcete přidat do výstupního souboru.  
  
## <a name="remarks"></a>Poznámky  
 Soubor prostředků Win32 lze vytvořit pomocí [kompilátoru prostředků](../../language-reference/compiler-options/resource-compiler-option.md). Nástroj Resource Compiler je vyvolán při kompilaci programu Visual C++; soubor .res je vytvořen ze souboru .rc.  
  
 Prostředek win32 může obsahovat informace o verzi nebo rastrové mapě (ikona), které by pomohly identifikovat vaši aplikaci v Průzkumníku souborů. Pokud nezadáte **-win32res**, kompilátor vygeneruje informace o verzi na základě verze sestavení.  
  
 Viz [-linkresource](./linkresource-compiler-option.md) (odkaz) nebo [-resource](./resource-compiler-option.md) (připojit) soubor prostředků rozhraní .NET Framework.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Aplikace.**  
  
3. Klikněte na tlačítko **Soubor prostředků** a zvolte soubor pomocí pole se seznamem.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` a připojení souboru `rf.res` prostředků `in.exe`Win32 k vytvoření :  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
