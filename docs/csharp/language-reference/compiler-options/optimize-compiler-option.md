---
title: "-optimize (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d74a338336d5878cb8d6f212076bb9f1eb7ef768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optimize-c-compiler-options"></a>/optimize (Možnosti kompilátoru C#)
**/ Optimize** možnost povolí nebo zakáže optimalizace provádí kompilátoru k vytvoření výstupního souboru menší, rychlejší a efektivnější.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a>Poznámky  
 **/ optimize** informuje o modul common language runtime optimalizovat kód za běhu.  
  
 Ve výchozím nastavení jsou zakázány optimalizace. Zadejte **/ optimize +** povolit optimalizace.  
  
 Při sestavování modulu, který bude používán sestavení, použijte stejný **/ optimize** nastavení jako sestavení.  
  
 **/o** je zkratka pro **/ optimize**.  
  
 Je možné kombinovat **/ optimize** a [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) možnosti.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Změnit **optimalizovat kód** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `t2.cs` a povolení optimalizace kompilátoru:  
  
```console  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
