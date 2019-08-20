---
title: -codepage (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: c85cd8935bcefd1353707624052b62ee982f7b07
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603047"
---
# <a name="-codepage-c-compiler-options"></a>-codepage (C# možnosti kompilátoru)
Tato možnost určuje, která znaková stránka se má použít při kompilaci, pokud požadovaná stránka není aktuální výchozí znakovou stránkou pro systém.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
 `id`  
 ID kódové stránky, která se má použít pro všechny soubory zdrojového kódu v kompilaci  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor se nejprve pokusí interpretovat všechny zdrojové soubory jako UTF-8. Pokud jsou soubory zdrojového kódu v kódování jiné než UTF-8 a používají jiné znaky než 7 bitů znaků ASCII, použijte možnost **-codepage** a určete, která znaková stránka má být použita. **-znaková stránka** se vztahuje na všechny soubory zdrojového kódu ve vaší kompilaci.  
    
 V tématu [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) najdete informace o tom, jak najít znakové stránky, které jsou v systému podporovány.  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
