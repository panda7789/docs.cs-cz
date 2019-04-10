---
title: -baseaddress (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: aa76e3d1d30e394f28b5112e45fc72229e9a78fc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295780"
---
# <a name="-baseaddress-c-compiler-options"></a>-baseaddress (možnosti kompilátoru C#)
**- Baseaddress** umožní zadat upřednostňované základní adrese, ve kterém se má načíst knihovnu DLL. Další informace o kdy a proč chcete použít tuto možnost najdete v tématu [Larry Osterman Weblogu](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
 `address`  
 Základní adresa pro knihovnu DLL. Tato adresa je zadat jako desítkové, hexadecimální nebo osmičkové číslo.  
  
## <a name="remarks"></a>Poznámky  
 Výchozí základní adresa knihovny DLL je nastavit modul common language runtime rozhraní .NET Framework.  
  
 Mějte na paměti, že se zaokrouhlí nižší řád slova v této adrese. Například pokud chcete zadat 0x11110001, to se zaokrouhlí na 0x11110000.  
  
 Dokončete proces podepisování pro knihovnu DLL pomocí sériové číslo. Soubor EXE s parametrem -R.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete v projektu **vlastnosti** stránky.  
  
2. Klikněte na tlačítko **sestavení** stránku vlastností.  
  
3. Klikněte na tlačítko **Upřesnit** tlačítko.  
  
4. Upravit **základní adresa knihovny DLL** vlastnost.  
  
     Programové nastavení tohoto parametru kompilátoru, naleznete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
