---
description: -Warn (možnosti kompilátoru C#)
title: -Warn (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: ab906912bc4bfab40e459c92a823b915240b8d55
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125082"
---
# <a name="-nowarn-c-compiler-options"></a>-Warn (možnosti kompilátoru C#)
Možnost **-s upozorněním** umožňuje potlačit, že kompilátor zobrazuje jedno nebo více upozornění. Více čísel upozornění oddělte čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Argumenty  
 `number1`, `number2`  
 Čísla upozornění, která má kompilátor potlačit.  
  
## <a name="remarks"></a>Poznámky  
 Měli byste zadat jenom číselnou část identifikátoru upozornění. Například pokud chcete potlačit CS0028, můžete zadat `-nowarn:28` .  
  
 Kompilátor bude tiše ignorovat čísla upozornění předaná do `-nowarn` , která byla platná v předchozích verzích, ale byla odebrána z kompilátoru. Například CS0679 byl platný v kompilátoru v aplikaci Visual Studio .NET 2002, ale byl následně odebrán.  
  
 Následující upozornění nelze potlačit pomocí `-nowarn` Možnosti:  
  
- Upozornění kompilátoru (úroveň 1) CS2002  
  
- Upozornění kompilátoru (úroveň 1) CS2023  
  
- Upozornění kompilátoru (úroveň 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu. Podrobnosti naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Upravte vlastnost **potlačit upozornění** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A> .  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Chyby kompilátoru C#](../compiler-messages/index.md)
