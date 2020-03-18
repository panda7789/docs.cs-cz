---
title: -baseaddress (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: f138f445b8a335c7505e25b34f560c4da40ab2dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937215"
---
# <a name="-baseaddress-c-compiler-options"></a>-baseaddress (Možnosti kompilátoru Jazyka C#)
Možnost **-baseaddress** umožňuje zadat upřednostňovanou základní adresu, na které chcete načíst dll. Další informace o tom, kdy a proč tuto možnost použít, naleznete v [tématu WebLog Larryho Ostermana](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Argumenty  
 `address`  
 Základní adresa pro dll. Tuto adresu lze zadat jako desetinné, šestnáctkové nebo osmičkové číslo.  
  
## <a name="remarks"></a>Poznámky  
 Výchozí základní adresa pro dll je nastavena za běhu mll .NET Framework common language.  
  
 Uvědomte si, že slovo nižšího řádu v této adrese bude zaokrouhleno. Pokud například zadáte 0x11110001, bude zaokrouhleno na 0x11110000.  
  
 Chcete-li dokončit proces podepisování pro DLL, použijte SN. EXE s volbou -R.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Sestavení.**  
  
3. Klepněte na tlačítko **Upřesnit.**  
  
4. Upravte vlastnost **Základní adresa DLL.**  
  
     Chcete-li tuto možnost kompilátoru nastavit programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
