---
description: -Optimize (možnosti kompilátoru C#)
title: -Optimize (možnosti kompilátoru C#)
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
ms.openlocfilehash: 6fd268414c4e54e7b4865733480f8917389015d0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125030"
---
# <a name="-optimize-c-compiler-options"></a>-Optimize (možnosti kompilátoru C#)
Možnost **-optimiz** povolí nebo zakáže optimalizace prováděné kompilátorem, aby byl výstupní soubor menší, rychlejší a efektivnější.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Poznámky  
 **– optimalizuje** také instruuje modul CLR (Common Language Runtime), aby optimalizoval kód za běhu.  
  
 Ve výchozím nastavení jsou optimalizace zakázané. Pokud chcete povolit optimalizace, zadejte **a optimalizujte +** .  
  
 Při sestavování modulu, který má být použit sestavením, použijte stejné nastavení **– optimalizovat** jako u sestavení.  
  
 **-o** je krátká forma typu **-optimize**.  
  
 Je možné kombinovat možnosti **-optimalizovat** a [-ladit](./debug-compiler-option.md) .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Upravte vlastnost **kód optimalizace** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A> .  
  
## <a name="example"></a>Příklad  
 Kompilovat `t2.cs` a povolit optimalizace kompilátoru:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
