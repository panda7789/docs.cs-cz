---
title: "-warnaserror (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0127f8982d4b8c487a7e243025052e3eb9a5ff75
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (možnosti kompilátoru C#)
**- Warnaserror +** možnost zpracovává všech upozornění jako chyby  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warnaserror[<U>+</U> | -][:warning-list]  
```  
  
## <a name="remarks"></a>Poznámky  
 Všechny zprávy, které by obvykle hlášeny jako upozornění jsou hlášeny jako chyby a procesu sestavení je zastaveno (žádný výstup, které jsou vytvořené soubory).  
  
 Ve výchozím nastavení **- warnaserror –** je v platnosti, což způsobí, že upozornění nezabrání generování výstupní soubor. **-warnaserror**, což je stejný jako **- warnaserror +**, způsobí, že upozornění jsou považovány za chyby.  
  
 Případně pokud chcete pouze několik konkrétní upozornění jsou považovány za chyby, můžete určit seznam oddělený čárkami čísel upozornění považovat za chyby.  
  
 Použití [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) k určení úrovně upozornění, která má kompilátor zobrazovat. Použití [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) zakázat některé upozornění.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Změnit **považovat upozornění jako chyby** vlastnost.  
  
     Pokud chcete nastavit tuto možnost kompilátoru prostřednictvím kódu programu, najdete v části <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` kompilátor zobrazovat žádná upozornění:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
