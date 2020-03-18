---
title: -filealign (C# Možnosti kompilátoru)
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
ms.openlocfilehash: aed8b412ea1580f7dfa4f87333598d76a85b5e64
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603020"
---
# <a name="-filealign-c-compiler-options"></a>-filealign (C# Možnosti kompilátoru)
Volba **-filealign** umožňuje určit velikost oddílů ve výstupním souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Argumenty  
 `number`  
 Hodnota, která určuje velikost oddílů ve výstupním souboru. Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192. Tyto hodnoty jsou v bajtů.  
  
## <a name="remarks"></a>Poznámky  
 Každý oddíl bude zarovnán na hranici, která je násobkem hodnoty **-filealign.** Neexistuje žádné pevné výchozí nastavení. Pokud **-filealign** není zadán, soubor runtime společného jazyka vybere výchozí v době kompilace.  
  
 Zadáním velikosti oddílu ovlivníte velikost výstupního souboru. Změna velikosti oddílu může být užitečná pro programy, které budou spuštěny na menších zařízeních.  
  
 Pomocí [funkce DUMPBIN](/cpp/build/reference/dumpbin-options) můžete zobrazit informace o oddílech ve výstupním souboru.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Sestavení.**  
  
3. Klepněte na tlačítko **Upřesnit.**  
  
4. Upravte vlastnost **Zarovnání souborů.**  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
