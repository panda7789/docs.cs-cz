---
title: -warn (Možnosti kompilátoru Jazyka C#)
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
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 5b05e944a37e16fc1fcc422271be00c09a271a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602402"
---
# <a name="-warn-c-compiler-options"></a>-warn (Možnosti kompilátoru Jazyka C#)
Možnost **-warn** určuje úroveň upozornění, aby se měl kompilátor zobrazit.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Argumenty  
 `option`  
 Úroveň upozornění, kterou chcete zobrazit pro kompilaci: Nižší čísla zobrazují pouze upozornění vysoké závažnosti; vyšší čísla ukazují více varování. Platné hodnoty jsou 0-4:  
  
|Úroveň varování|Význam|  
|-------------------|-------------|  
|0|Vypne emise všech varovných zpráv.|  
|1|Zobrazí závažné varovné zprávy.|  
|2|Zobrazí upozornění úrovně 1 a určitá méně závažná upozornění, například upozornění na skrytí členů třídy.|  
|3|Zobrazí upozornění úrovně 2 a určitá méně závažná upozornění, například `false`upozornění na výrazy, které jsou vždy vyhodnoceny nebo `true` .|  
|4 (výchozí nastavení)|Zobrazí všechna upozornění úrovně 3 a informační upozornění.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat informace o chybě nebo upozornění, můžete vyhledat kód chyby v indexu nápovědy. Další způsoby získání informací o chybě nebo upozornění naleznete v tématu [C# Compiler Errors](../compiler-messages/index.md).  
  
 Použití [-warnaserror](./warnaserror-compiler-option.md) považovat všechna upozornění jako chyby. Pomocí [funkce -nowarn](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.  
  
 **-w** je krátká forma **-warn**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Sestavení.**  
  
3. Upravte vlastnost **Úroveň upozornění.**  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Zkompilujte `in.cs` a mají kompilátor pouze zobrazení úrovně 1 upozornění:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
