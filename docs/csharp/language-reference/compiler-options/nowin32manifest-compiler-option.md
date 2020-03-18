---
title: -nowin32manifest (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602711"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (Možnosti kompilátoru Jazyka C#)
Pomocí možnosti **-nowin32manifest** můžete kompilátoru dát pokyn, aby do spustitelného souboru nevkládal žádný manifest aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud je tato možnost použita, bude aplikace předmětem virtualizace v systému Windows Vista, pokud nezadáte manifest aplikace v souboru prostředků Win32 nebo během pozdějšího kroku sestavení.  
  
 V sadě Visual Studio nastavte tuto možnost na stránce **Vlastnosti aplikace** výběrem **možnosti Vytvořit aplikaci bez manifestu** v rozevíracím seznamu **Manifest.** Další informace naleznete v [tématu Stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Další informace o vytvoření manifestu naleznete v tématu [-win32manifest (C# Compiler Options).](./win32manifest-compiler-option.md)  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
