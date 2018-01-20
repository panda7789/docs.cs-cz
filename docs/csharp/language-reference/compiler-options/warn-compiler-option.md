---
title: "-warn (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a1f2c55aa078adb213a93dc5aff7ced40793bfa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-warn-c-compiler-options"></a>-warn (možnosti kompilátoru C#)
**-Warn** možnost určuje úroveň pro upozornění pro kompilátor zobrazovat.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Arguments  
 `option`  
 Úroveň pro upozornění, které chcete zobrazit pro kompilace: nižší čísla zobrazují pouze vysokou závažností upozornění; vyšší čísla zobrazit další varování. Platné hodnoty jsou 0-4:  
  
|Úroveň upozornění|Význam|  
|-------------------|-------------|  
|0|Vypne vyvolávání všechny zprávy upozornění.|  
|1|Zobrazí závažné zprávy upozornění.|  
|2|Zobrazí upozornění úrovně 1 a některé méně závažné upozornění, jako jsou třeba upozornění o skrývání členy třídy.|  
|3|Zobrazí upozornění úrovně 2 a některé méně závažné upozornění, jako jsou třeba upozornění o výrazech, které jsou vždy vyhodnoceny na `true` nebo `false`.|  
|4 (výchozí)|Zobrazí všechny úrovně 3 upozornění a informační upozornění.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat informace o chybě nebo upozornění, můžete vyhledat kód chyby v rejstříku nápovědy. Další způsoby, jak získat informace o chybě nebo upozornění, naleznete v části [chyby kompilátoru jazyka C#](../../../csharp/language-reference/compiler-messages/index.md).  
  
 Použití [- warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) zachází všech upozornění jako chyby. Použití [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) zakázat některé upozornění.  
  
 **-w** je zkratka pro **-warn**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Změnit **úroveň pro upozornění** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` kompilátor zobrazuje pouze upozornění úrovně 1:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
