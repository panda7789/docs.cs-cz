---
title: -nostdlib (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 1dc0ab70ca28626c4a3f505c13ec1d6f828a4b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216132"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (možnosti kompilátoru C#)
**-nostdlib** zabraňuje importu mscorlib.dll, která definuje obor názvů, celý systém.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nostdlib[+ | -]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte, pokud chcete definovat nebo vytvořit vlastní System – obor názvů a objekty.  
  
 Pokud nezadáte **- nostdlib**, mscorlib.dll bude importována do programu (totéž jako zadání **- nostdlib –**). Určení **- nostdlib** je stejné jako zadání **- nostdlib +**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete **vlastnosti** stránky pro projekt.  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Klikněte **Upřesnit** tlačítko.  
  
4.  Změnit **Neodkazovat mscorlib.dll** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
