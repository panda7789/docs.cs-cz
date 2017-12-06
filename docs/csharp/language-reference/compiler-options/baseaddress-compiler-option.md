---
title: "-baseaddress (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f8cc5e19565a0e5044626c4fb8eb9d684fbe0a73
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2017
---
# <a name="baseaddress-c-compiler-options"></a>/baseaddress (Možnosti kompilátoru C#)
**/BaseAddress** možnost umožňuje zadat upřednostňovaná základní adresa, na které se mají načíst knihovnu DLL. Další informace o kdy a proč použít tuto možnost najdete v tématu [Larry Osterman-blog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
 `address`  
 Základní adresa pro knihovnu DLL. Tuto adresu můžete zadat hodnotu decimal, šestnáctkovém nebo osmičkové číslo.  
  
## <a name="remarks"></a>Poznámky  
 Výchozí základní adresy knihovny DLL je nastavena pomocí modulu CLR rozhraní .NET Framework.  
  
 Mějte na paměti se zaokrouhlí na slovo nižší pořadí v tuto adresu. Například pokud zadáte 0x11110001, ji budou zaokrouhlí 0x11110000.  
  
 Chcete-li dokončit proces podepisování pro knihovny DLL, použijte SN. EXE s parametrem -R.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Klikněte **Upřesnit** tlačítko.  
  
4.  Změnit **základní adresa knihovny DLL** vlastnost.  
  
     Pokud chcete nastavit tuto možnost kompilátoru prostřednictvím kódu programu, najdete v části <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
