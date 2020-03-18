---
title: -nowarn (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: fa3079bf1431ba1a16b5a2eef0dd5500fe95909c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606611"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (Možnosti kompilátoru Jazyka C#)
Možnost **-nowarn** umožňuje potlačit kompilátor z zobrazení jednoho nebo více upozornění. Oddělte více výstražných čísel čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Argumenty  
 `number1`, `number2`  
 Číslo upozornění, které chcete, aby kompilátor potlačit.  
  
## <a name="remarks"></a>Poznámky  
 Měli byste zadat pouze číselnou část identifikátoru upozornění. Chcete-li například potlačit cs0028, můžete `-nowarn:28`zadat .  
  
 Kompilátor bude tiše ignorovat čísla `-nowarn` upozornění předaná, která byla platná v předchozích verzích, ale která byla odebrána z kompilátoru. Například CS0679 byl platný v kompilátoru v sadě Visual Studio .NET 2002, ale byl následně odebrán.  
  
 Následující upozornění nelze potlačit `-nowarn` možností:  
  
- Upozornění kompilátoru (úroveň 1) CS2002  
  
- Upozornění kompilátoru (úroveň 1) CS2023  
  
- Upozornění kompilátoru (úroveň 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu. Podrobnosti naleznete v [tématu Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Klikněte na stránku vlastností **Sestavení.**  
  
3. Upravte vlastnost **Potlačit upozornění.**  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Chyby kompilátoru jazyka C#](../compiler-messages/index.md)
