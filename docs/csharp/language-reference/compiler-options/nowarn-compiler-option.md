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
ms.openlocfilehash: 1c5e8bc7ad065c4662cd489930b2226e8a4b8962
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (možnosti kompilátoru C#)
**- Nowarn** možnost umožňuje potlačit kompilátoru zobrazování jeden nebo více upozornění. Více čísel upozornění oddělte čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Arguments  
 `number1`, `number2`  
 Upozornění čísel, které chcete kompilátorem potlačit.  
  
## <a name="remarks"></a>Poznámky  
 Měli byste zadat pouze číselnou část identifikátor upozornění. Například pokud chcete potlačit CS0028, můžete zadat `-nowarn:28`.  
  
 Kompilátor bude tiše ignorovat čísla upozornění předaná `-nowarn` , které byly v předchozích verzích platný, ale které byly odebrány z kompilátoru. Například CS0679 platné v kompilátoru v sadě Visual Studio .NET 2002 ale následně bylo odebráno.  
  
 Následující upozornění nelze potlačit pomocí `-nowarn` možnost:  
  
-   CS2002 kompilátoru upozornění (úroveň 1)  
  
-   CS2023 kompilátoru upozornění (úroveň 1)  
  
-   CS2029 kompilátoru upozornění (úroveň 1)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete **vlastnosti** stránky pro projekt. Podrobnosti najdete v tématu [stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Změnit **potlačit upozornění** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
 [Chyby kompilátoru jazyka C#](../../../csharp/language-reference/compiler-messages/index.md)
