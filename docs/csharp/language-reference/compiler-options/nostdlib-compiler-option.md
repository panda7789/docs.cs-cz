---
title: "-nostdlib (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dd9d2b6a4a9c774aa339e840ad0020ee39cb10d3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
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
