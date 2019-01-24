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
ms.openlocfilehash: 7cbd3ec1b2d134106c6c9429341f5603444dac27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693977"
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
 Pokud kompilujete jeden nebo více souborů zdrojového kódu, které nebyly vytvořeny v počítači použít výchozí znakové stránky, můžete použít **- znaková stránka** možnost zadat znakovou stránku, která se má použít. **-codepage** se vztahuje na všechny soubory zdrojového kódu v kompilaci.  
  
 Pokud se stejnou znakovou stránku, která je v platnosti v počítači byly vytvořeny soubory zdrojového kódu nebo pokud soubory zdrojového kódu byly vytvořeny pomocí UNICODE nebo UTF-8, není nutné použít **- znaková stránka**.  
  
 Zobrazit [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) informace o tom, jak najít kódu stránky jsou podporovány v systému.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
