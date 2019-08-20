---
title: -align (C# možnosti kompilátoru)
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
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603020"
---
# <a name="-filealign-c-compiler-options"></a>-align (C# možnosti kompilátoru)
Možnost **-souboru align** umožňuje určit velikost oddílů ve výstupním souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Hodnota, která určuje velikost oddílů ve výstupním souboru. Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192. Tyto hodnoty jsou v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Každý oddíl bude zarovnán na hranici, která je násobkem hodnoty **Zarovnání** . Neexistuje žádná pevná výchozí hodnota. Pokud parametr není zadán, modul CLR (Common Language Runtime) vybere výchozí hodnotu v době kompilace.  
  
 Když zadáte velikost oddílu, ovlivníte velikost výstupního souboru. Změna velikosti oddílu může být užitečná pro programy, které se spustí na menších zařízeních.  
  
 Pomocí služby [DUMPBIN](/cpp/build/reference/dumpbin-options) můžete zobrazit informace o oddílech ve výstupním souboru.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Klikněte na tlačítko **Upřesnit** .  
  
4. Upravte vlastnost **Zarovnání souboru** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>v tématu.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
