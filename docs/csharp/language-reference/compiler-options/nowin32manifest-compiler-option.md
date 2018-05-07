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
ms.openlocfilehash: a07ead99ddd4e230fff8d1452ef81171ed849b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (možnosti kompilátoru C#)
Použití **-nowin32manifest** – možnost kompilátoru není pro vložení jakýkoli manifest aplikace do spustitelného souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud tato možnost se používá, aplikace budou platit virtualizace v systému Windows Vista Pokud není poskytnut manifest aplikace v souboru Win32 prostředků nebo v pozdějším kroku sestavení.  
  
 V sadě Visual Studio, nastavte tuto možnost **vlastnosti aplikace** stránky tak, že vyberete **vytvořit aplikaci bez manifestu** možnost **Manifest** rozevíracím seznamu. Další informace najdete v tématu [stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Další informace o vytváření manifestu najdete v tématu [-win32manifest (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
