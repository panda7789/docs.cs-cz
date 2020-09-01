---
description: -Warn (možnosti kompilátoru C#)
title: -Warn (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 55e80d0bd05e2119154210503bb277d743050e18
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139070"
---
# <a name="-warn-c-compiler-options"></a>-Warn (možnosti kompilátoru C#)
Možnost **-warn** určuje úroveň upozornění, která má kompilátor zobrazovat.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Argumenty  
 `option`  
 Úroveň upozornění, kterou chcete zobrazit pro kompilaci: nižší čísla zobrazují pouze upozornění s vysokou závažností; vyšší čísla zobrazují více upozornění. Hodnota musí být nula nebo kladné celé číslo:

|Úroveň upozornění|Význam|
|-------------------|-------------|
|0|Vypne emise všech varovných zpráv.|
|1|Zobrazí závažné varovné zprávy.|  
|2|Zobrazí upozornění úrovně 1 a některá, méně závažná upozornění, například upozornění na skrývání členů třídy.|  
|3|Zobrazí upozornění úrovně 2 plus určitá méně závažná upozornění, například upozornění na výrazy, které vždy vyhodnotí `true` nebo `false` .|  
|4 (výchozí)|Zobrazí všechna upozornění úrovně 3 a informační upozornění.|
|5|Zobrazí upozornění úrovně 4 a [Další upozornění](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) z kompilátoru dodaného s C# 9,0.|
|Větší než 5|Jakákoli hodnota vyšší než 5 bude zpracována jako 5. Obecně umísťujete libovolnou velkou hodnotu (například), `9999` abyste měli jistotu, že budete mít vždy všechna upozornění, pokud je kompilátor aktualizován novými úrovněmi upozornění.|
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat informace o chybě nebo upozornění, můžete vyhledat kód chyby v indexu Nápověda. Další způsoby, jak získat informace o chybě nebo upozornění, najdete v tématu [chyby kompilátoru jazyka C#](../compiler-messages/index.md).  
  
 Pomocí [-warnaserror –](./warnaserror-compiler-option.md) považovat všechna upozornění za chyby. Pomocí [-Upozornění](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.  
  
 **-w** je krátká forma **varování**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Upravte vlastnost **úroveň upozornění** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A> .  
  
## <a name="example"></a>Příklad  
 Kompilovat `in.cs` a mít jenom zobrazení upozornění úrovně 1 pro kompilátor:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
