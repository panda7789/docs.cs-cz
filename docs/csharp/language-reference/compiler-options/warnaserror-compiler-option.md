---
title: -warnaserror (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 2ae555c2e049e687f508e62b5b46fd8a744e827f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329100"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (možnosti kompilátoru C#)
**- Warnaserror +** možnost zpracuje všechna upozornění jako chyby  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Poznámky  
 Všechny zprávy, které by obvykle hlášeny jako varování jsou hlášeny jako chyby a proces sestavení je zastavení (žádné výstupní soubory jsou vytvořeny).  
  
 Ve výchozím nastavení **- warnaserror –** je v platnosti, což způsobí, že upozornění nezabrání generování výstupního souboru. **-warnaserror**, což je stejná jako **- warnaserror +**, způsobí upozornění budou považována za chyby.  
  
 Pokud chcete pouze několik specifická upozornění budou považována za chyby, můžete volitelně zadat čárkou oddělený seznam čísel upozornění pro nakládání s chybami.  
  
 Použití [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) k určení úrovně upozornění, která má kompilátor pro zobrazení. Použití [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) zakázat určitá upozornění.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete v projektu **vlastnosti** stránky.  
  
2. Klikněte na tlačítko **sestavení** stránku vlastností.  
  
3. Upravit **zpracovávat upozornění jako chyby** vlastnost.  
  
 Programové nastavení tohoto parametru kompilátoru, naleznete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` kompilátor zobrazovat žádné upozornění:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
