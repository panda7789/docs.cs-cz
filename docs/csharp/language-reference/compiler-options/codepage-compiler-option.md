---
title: -codepage (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 59dc1abc3f678a4cf15543c11f9f200ff318ce8f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876930"
---
# <a name="-codepage-c-compiler-options"></a>-codepage (možnosti kompilátoru C#)
Tato možnost určuje, které znakovou stránku pro použití během kompilace, pokud se požadovaná stránka není aktuální výchozí znakovou stránku, která pro systém.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
 `id`  
 Id stránky kód pro všechny soubory zdrojového kódu dané kompilace.  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor se nejprve pokusí interpretovat všechny zdrojové soubory jako UTF-8. Pokud soubory zdrojového kódu jsou v kódování jiné než v kódování UTF-8 a použijte jiné znaky než 7bitových znaků ASCII, použijte **- znaková stránka** možnost zadat znakovou stránku, která se má použít. **-codepage** se vztahuje na všechny soubory zdrojového kódu v kompilaci.  
    
 Zobrazit [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) informace o tom, jak najít kódu stránky jsou podporovány v systému.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
