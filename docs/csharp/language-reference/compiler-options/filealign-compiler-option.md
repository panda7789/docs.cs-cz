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
ms.openlocfilehash: 39b5aeecba39c0e5377fd4f76902dae4b678c324
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530399"
---
# <a name="-filealign-c-compiler-options"></a>-filealign (možnosti kompilátoru C#)
**- Filealign** možnost umožňuje zadat velikost oddíly výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Hodnota, která určuje velikost oddíly výstupního souboru. Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192. Tyto hodnoty jsou v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Každý oddíl se zarovnáno na hranici, která je násobkem **- filealign** hodnotu. Neexistuje žádná pevná výchozí hodnota. Pokud **- filealign** není zadán, modul common language runtime zvolí výchozí v době kompilace.  
  
 Tak, že určíte velikost oddílu, vliv na velikost výstupního souboru. Změna velikosti oddílu může být užitečné pro programy, které poběží na menších zařízeních.  
  
 Použití [DUMPBIN](/cpp/build/reference/dumpbin-options) zobrazíte informace o oddílech výstupního souboru.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **vlastnosti** stránky.  
  
2.  Klikněte na tlačítko **sestavení** stránku vlastností.  
  
3.  Klikněte na tlačítko **Upřesnit** tlačítko.  
  
4.  Upravit **zarovnání souboru** vlastnost.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
