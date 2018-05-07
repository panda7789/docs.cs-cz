---
title: -filealign (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
ms.openlocfilehash: d51dd0d63bec251d879ffb5e59ce5f7edaf136b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-filealign-c-compiler-options"></a>-filealign (možnosti kompilátoru C#)
**- Filealign** možnost umožňuje zadat velikost oddílů ve výstupním souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Hodnota, která určuje velikost oddílů ve výstupním souboru. Platné hodnoty jsou 512, 1024, 2048, 4096 až 8192. Tyto hodnoty jsou v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Každý oddíl bude zarovnán na hranici, která je násobkem **- filealign** hodnotu. Neexistuje žádná pevná výchozí hodnota. Pokud **- filealign** není zadán, modul common language runtime zvolí výchozí v době kompilace.  
  
 Zadáním velikost části vliv velikost výstupního souboru. Změna velikosti oddílu může být užitečné pro programy, které se spustí na menší zařízení.  
  
 Použití [DUMPBIN](/cpp/build/reference/dumpbin-options) zobrazíte informace o oddílech ve výstupním souboru.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Klikněte **Upřesnit** tlačítko.  
  
4.  Změnit **zarovnání souboru** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
