---
title: -nowin32manifest (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602711"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (C# možnosti kompilátoru)
Pomocí možnosti **-nowin32manifest** dejte kompilátoru pokyn, aby nevložil žádný manifest aplikace do spustitelného souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud použijete tuto možnost, bude se aplikace vztahovat k virtualizaci v systému Windows Vista, pokud neposkytnete manifest aplikace v souboru prostředků Win32 nebo během pozdějšího kroku sestavení.  
  
 V sadě Visual Studio nastavte tuto možnost na stránce **vlastností aplikace** výběrem možnosti **vytvořit aplikaci bez manifestu** v rozevíracím seznamu **manifest** . Další informace naleznete na [stránce aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Další informace o vytváření manifestu naleznete v tématu [-win32manifest (C# možnosti kompilátoru)](./win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
