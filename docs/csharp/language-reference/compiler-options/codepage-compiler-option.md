---
title: -codepage (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 3352e7fc446ace391540360a3b6b36d604ca5f13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173754"
---
# <a name="-codepage-c-compiler-options"></a>-codepage (C# Možnosti kompilátoru)
Tato možnost určuje, kterou znakovou stránku použít během kompilace, pokud požadovaná stránka není aktuální výchozí znakovou stránkou systému.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Argumenty  
 `id`  
 Id znakové stránky, která má být používána pro všechny soubory zdrojového kódu v kompilaci.  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor se nejprve pokusí interpretovat všechny zdrojové soubory jako UTF-8. Pokud jsou soubory zdrojového kódu v jiném kódování než UTF-8 a používají jiné znaky než 7bitové znaky ASCII, použijte možnost **-codepage** k určení, která znaková stránka má být použita. **-codepage** se vztahuje na všechny soubory zdrojového kódu ve vaší kompilaci.  

 Informace o tom, jak zjistit, které znakové stránky jsou ve vašem systému podporované, najdete v tématu [GetCPInfo.](/windows/desktop/api/winnls/nf-winnls-getcpinfo)  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
