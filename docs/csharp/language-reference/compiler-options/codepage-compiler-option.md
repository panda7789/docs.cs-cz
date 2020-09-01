---
description: -codepage (možnosti kompilátoru C#)
title: -codepage (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 4c812314ed9c1abcd7d2f34b2281140175621312
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125953"
---
# <a name="-codepage-c-compiler-options"></a>-codepage (možnosti kompilátoru C#)
Tato možnost určuje, která znaková stránka se má použít při kompilaci, pokud požadovaná stránka není aktuální výchozí znakovou stránkou pro systém.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Argumenty  
 `id`  
 ID kódové stránky, která se má použít pro všechny soubory zdrojového kódu v kompilaci  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor se nejprve pokusí interpretovat všechny zdrojové soubory jako UTF-8. Pokud jsou soubory zdrojového kódu v kódování jiné než UTF-8 a používají jiné znaky než 7 bitů znaků ASCII, použijte možnost **-codepage** a určete, která znaková stránka má být použita. **-znaková stránka** se vztahuje na všechny soubory zdrojového kódu ve vaší kompilaci.  

 V tématu [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) najdete informace o tom, jak najít znakové stránky, které jsou v systému podporovány.  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
