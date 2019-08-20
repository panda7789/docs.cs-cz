---
title: -Warn (C# možnosti kompilátoru)
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
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602402"
---
# <a name="-warn-c-compiler-options"></a>-Warn (C# možnosti kompilátoru)
Možnost **-warn** určuje úroveň upozornění, která má kompilátor zobrazovat.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Arguments  
 `option`  
 Úroveň upozornění, kterou chcete zobrazit pro kompilaci: Nižší čísla zobrazují pouze upozornění s vysokou závažností; vyšší čísla zobrazují více upozornění. Platné hodnoty jsou 0-4:  
  
|Úroveň upozornění|Význam|  
|-------------------|-------------|  
|0|Vypne emise všech varovných zpráv.|  
|1|Zobrazí závažné varovné zprávy.|  
|2|Zobrazí upozornění úrovně 1 a některá, méně závažná upozornění, například upozornění na skrývání členů třídy.|  
|3|Zobrazí upozornění úrovně 2 plus určitá méně závažná upozornění, například upozornění na `true` výrazy, které vždy vyhodnotí nebo. `false`|  
|4 (výchozí)|Zobrazí všechna upozornění úrovně 3 a informační upozornění.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat informace o chybě nebo upozornění, můžete vyhledat kód chyby v indexu Nápověda. Další způsoby, jak získat informace o chybě nebo upozornění, najdete v tématu [ C# chyby kompilátoru](../compiler-messages/index.md).  
  
 Pomocí [-warnaserror –](./warnaserror-compiler-option.md) považovat všechna upozornění za chyby. Pomocí [-Upozornění](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.  
  
 **-w** je krátká forma **varování**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Upravte vlastnost **úroveň upozornění** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>v tématu.  
  
## <a name="example"></a>Příklad  
 Kompilovat `in.cs` a mít jenom zobrazení upozornění úrovně 1 pro kompilátor:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
