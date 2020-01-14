---
title: -BaseAddress (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: f138f445b8a335c7505e25b34f560c4da40ab2dd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937215"
---
# <a name="-baseaddress-c-compiler-options"></a>-BaseAddress (C# možnosti kompilátoru)
Možnost **-BaseAddress** umožňuje zadat upřednostňovanou základní adresu, na které se má načíst knihovna DLL. Další informace o tom, kdy a proč použít tuto možnost, najdete v tématu [blog Larry Osterman](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
 `address`  
 Základní adresa knihovny DLL. Tuto adresu lze zadat jako desítkové, šestnáctkové nebo osmičkové číslo.  
  
## <a name="remarks"></a>Poznámky  
 Výchozí základní adresa pro knihovnu DLL je nastavena .NET Framework modul CLR (Common Language Runtime).  
  
 Uvědomte si, že slovo v této adrese bude zaokrouhleno. Pokud například zadáte 0x11110001, bude se zaokrouhlit na 0x11110000.  
  
 Chcete-li dokončit proces podepisování pro knihovnu DLL, použijte SN. EXE s parametrem-R.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Klikněte na tlačítko **Upřesnit** .  
  
4. Upravte vlastnost **základní adresy knihovny DLL** .  
  
     Chcete-li nastavit tuto možnost kompilátoru programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
