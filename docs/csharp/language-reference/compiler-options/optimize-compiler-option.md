---
title: -optimalizovat (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: bec99ca582070a99fd8b734ef8a7b9e71d945488
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606596"
---
# <a name="-optimize-c-compiler-options"></a>-optimalizovat (Možnosti kompilátoru Jazyka C#)
Možnost **-optimize** umožňuje nebo zakáže optimalizace prováděné kompilátorem, aby byl výstupní soubor menší, rychlejší a efektivnější.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Poznámky  
 **-optimize** také říká, že společný jazyk runtime pro optimalizaci kódu za běhu.  
  
 Ve výchozím nastavení jsou optimalizace zakázány. Zadejte **-optimize+** pro povolení optimalizace.  
  
 Při vytváření modulu, který má být používán sestavením, použijte stejné nastavení **optimalizace** jako nastavení sestavy.  
  
 **-o** je krátká forma **-optimize**.  
  
 Je možné kombinovat možnosti **-optimize** a [-debug.](./debug-compiler-option.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Sestavení.**  
  
3. Upravte vlastnost **Optimalizovat kód.**  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Kompilace `t2.cs` a povolení optimalizace kompilátoru:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
