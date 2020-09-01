---
description: -nowin32manifest (možnosti kompilátoru C#)
title: -nowin32manifest (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8514ab5b118e320d456d1b7367fab3b463c3607a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125056"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (možnosti kompilátoru C#)
Pomocí možnosti **-nowin32manifest** dejte kompilátoru pokyn, aby nevložil žádný manifest aplikace do spustitelného souboru.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud použijete tuto možnost, bude se aplikace vztahovat k virtualizaci v systému Windows Vista, pokud neposkytnete manifest aplikace v souboru prostředků Win32 nebo během pozdějšího kroku sestavení.  
  
 V sadě Visual Studio nastavte tuto možnost na stránce **vlastností aplikace** výběrem možnosti **vytvořit aplikaci bez manifestu** v rozevíracím seznamu **manifest** . Další informace naleznete na [stránce aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Další informace o vytváření manifestu naleznete v tématu [-win32manifest (možnosti kompilátoru C#)](./win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
