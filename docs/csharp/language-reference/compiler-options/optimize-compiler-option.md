---
title: -optimize (možnosti kompilátoru C#)
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
ms.openlocfilehash: 92d5faa870623b5b7d7d1bad16ad0f1ba3f1bf76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636992"
---
# <a name="-optimize-c-compiler-options"></a>-optimize (možnosti kompilátoru C#)
**– Optimalizace** možnost povolí nebo zakáže optimalizace provedené kompilátorem za účelem zkontrolujte výstupní soubor menší, rychlejší a efektivnější.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Poznámky  
 **-optimize** také říká modul common language runtime k optimalizaci kódu za běhu.  
  
 Ve výchozím nastavení jsou zakázané optimalizace. Zadejte **– optimalizace +** povolíte optimalizace.  
  
 Při vytváření modulu pro sestavení, použijte stejný **– optimalizace** nastavení jako sestavení.  
  
 **-o** je zkratka pro **– optimalizace**.  
  
 Je možné kombinovat **– optimalizace** a [– ladění](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) možnosti.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **vlastnosti** stránky.  
  
2.  Klikněte na tlačítko **sestavení** stránku vlastností.  
  
3.  Upravit **optimalizovat kód** vlastnost.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `t2.cs` a povolení optimalizace kompilátoru:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
