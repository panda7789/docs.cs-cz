---
title: "-codepage (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1e17622256ca6a0344797ba16e007ba6feb8f873
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2017
---
# <a name="codepage-c-compiler-options"></a>/codepage (Možnosti kompilátoru C#)
Tato možnost určuje, které znakovou stránku pro použití během kompilace, pokud se požadovaná stránka není aktuální výchozí znaková stránka pro systém.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
 `id`  
 Id znaková stránka pro všechny soubory zdrojového kódu v kompilace.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je jeden nebo více soubory zdrojového kódu, které nebyly vytvořeny používat výchozí znakovou stránku ve vašem počítači, můžete použít **/CODEPAGE** možnost zadat znakovou stránku, která má být použita. **/ codePage** se vztahuje na všechny soubory zdrojového kódu v kompilaci.  
  
 Pokud soubory zdrojového kódu, které byly vytvořeny pomocí stejné znakové stránky, která je umístěna ve vašem počítači nebo pokud soubory zdrojového kódu se vytvořily s UNICODE nebo UTF-8, není nutné použít **/CODEPAGE**.  
  
 V tématu [GetCPInfo](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) informace o tom, jak najít které kódu stránky jsou podporovány v systému.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
