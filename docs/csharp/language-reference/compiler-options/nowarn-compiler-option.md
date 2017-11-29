---
title: "-nowarn (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 499203bb4714fa2d07b2c0e42958ffd0e472facc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nowarn-c-compiler-options"></a>/nowarn (Možnosti kompilátoru C#)
**/Nowarn** možnost umožňuje potlačit kompilátoru zobrazování jeden nebo více upozornění. Více čísel upozornění oddělte čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Arguments  
 `number1`, `number2`  
 Upozornění čísel, které chcete kompilátorem potlačit.  
  
## <a name="remarks"></a>Poznámky  
 Měli byste zadat pouze číselnou část identifikátor upozornění. Například pokud chcete potlačit CS0028, můžete zadat `/nowarn:28`.  
  
 Kompilátor bude tiše ignorovat čísla upozornění předaná `/nowarn` , které byly v předchozích verzích platný, ale které byly odebrány z kompilátoru. Například CS0679 platné v kompilátoru v sadě Visual Studio .NET 2002 ale následně bylo odebráno.  
  
 Následující upozornění nelze potlačit pomocí `/nowarn` možnost:  
  
-   CS2002 kompilátoru upozornění (úroveň 1)  
  
-   CS2023 kompilátoru upozornění (úroveň 1)  
  
-   CS2029 kompilátoru upozornění (úroveň 1)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete **vlastnosti** stránky pro projekt. Podrobnosti najdete v tématu [stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Změnit **potlačit upozornění** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
 [Chyby kompilátoru jazyka C#](../../../csharp/language-reference/compiler-messages/index.md)
