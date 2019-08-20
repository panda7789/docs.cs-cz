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
ms.openlocfilehash: e96ab3ece6edc36c913a8efc0097ff9c4a1e3c22
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69607028"
---
# <a name="-baseaddress-c-compiler-options"></a>-BaseAddress (C# možnosti kompilátoru)
Možnost **-BaseAddress** umožňuje zadat upřednostňovanou základní adresu, na které se má načíst knihovna DLL. Další informace o tom, kdy a proč použít tuto možnost, najdete v tématu [blog Larry Osterman](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).  
  
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
  
     Chcete-li nastavit tuto možnost kompilátoru programově <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>, přečtěte si téma.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
