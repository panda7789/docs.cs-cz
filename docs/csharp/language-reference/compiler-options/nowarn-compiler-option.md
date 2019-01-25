---
title: -nowarn (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 79d61e7e4096ab206e207a05553a68020bca6204
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664821"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (možnosti kompilátoru C#)
**- Nowarn** možnost umožňuje potlačit zobrazování upozornění na jeden nebo více kompilátorem. Více čísel upozornění oddělte čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Arguments  
 `number1`, `number2`  
 Čísla upozornění, která má kompilátor potlačit.  
  
## <a name="remarks"></a>Poznámky  
 Měli byste zadat pouze číselnou část identifikátoru upozornění. Například pokud chcete potlačit CS0028, budete moci zadat `-nowarn:28`.  
  
 Kompilátor bude tiše ignorovat upozornění čísla předaná `-nowarn` , která byla platná v předchozích verzích, ale které byly odebrány z kompilátoru. Například CS0679 byla platná v kompilátoru v sadě Visual Studio .NET 2002, ale později byl odebrán.  
  
 Nelze potlačit následující upozornění `-nowarn` možnost:  
  
-   Kompilátor CS2002 upozornění (úroveň 1)  
  
-   Kompilátor CS2023 upozornění (úroveň 1)  
  
-   Kompilátor CS2029 upozornění (úroveň 1)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřít **vlastnosti** stránky pro projekt. Podrobnosti najdete v tématu [stránku sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Klikněte na tlačítko **sestavení** stránku vlastností.  
  
3.  Upravit **potlačit upozornění** vlastnost.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Chyby kompilátoru jazyka C#](../../../csharp/language-reference/compiler-messages/index.md)
