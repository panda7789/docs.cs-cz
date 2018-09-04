---
title: -nowin32manifest (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 3ab52d541c169850f6ae7ba7e7cfded290f890e7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530506"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (možnosti kompilátoru C#)
Použití **-nowin32manifest** možnost dát pokyn kompilátoru, aby jakýkoli manifest aplikace pro vložení do spustitelného souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Poznámky  
 Při použití této možnosti aplikace se budou řídit virtualizace v systému Windows Vista, pokud nezadáte manifest aplikace do souboru prostředků Win32 nebo v pozdějším kroku sestavení.  
  
 V sadě Visual Studio, nastavte tuto možnost **vlastnost aplikace** stránky tak, že vyberete **vytvořit aplikaci bez manifestu** možnost **Manifest** rozevírací seznam. Další informace najdete v tématu [stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Další informace o vytváření manifestu naleznete v tématu [-win32manifest (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
