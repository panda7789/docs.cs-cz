---
title: "-win32res (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 96583542c62305cbaa5a24f66e9e54ec9b525c90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="win32res-c-compiler-options"></a>/win32res (Možnosti kompilátoru C#)
**/Win32res** možnost vloží prostředek systému Win32 ve výstupním souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/win32res:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Soubor prostředků, který chcete přidat do výstupního souboru.  
  
## <a name="remarks"></a>Poznámky  
 Zdrojového souboru Win32 může být vytvořen pomocí [kompilátor prostředků](../../language-reference/compiler-options/resource-compiler-option.md). Nástroj Resource Compiler je vyvolán při kompilaci programu Visual C++; soubor .res je vytvořen ze souboru .rc.  
  
 Win32 prostředků může obsahovat verzi nebo rastrový obrázek (ikona) informace, které pomohou identifikovat aplikace v Průzkumníkovi souborů. Pokud nezadáte **/win32res**, kompilátor vygeneruje informace o verzi na základě verze sestavení.  
  
 V tématu [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (pro referenční dokumentace) nebo [/Resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (pro připojení) souboru prostředků rozhraní .NET Framework.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **aplikace** stránku vlastností.  
  
3.  Klikněte na **souboru prostředků** tlačítko a zvolte soubor pomocí pole se seznamem.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` a připojte soubor prostředků Win32 `rf.res` k vytvoření `in.exe`:  
  
```console  
csc /win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
