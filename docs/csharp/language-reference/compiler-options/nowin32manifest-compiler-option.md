---
title: "-nowin32manifest (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1e0d4697e0e14c84c4bc642521cf4f9cdf6a4ed6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nowin32manifest-c-compiler-options"></a>/nowin32manifest (Možnosti kompilátoru C#)
Použití **/nowin32manifest** – možnost kompilátoru není pro vložení jakýkoli manifest aplikace do spustitelného souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/nowin32manifest  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud tato možnost se používá, aplikace budou platit virtualizace v systému Windows Vista Pokud není poskytnut manifest aplikace v souboru Win32 prostředků nebo v pozdějším kroku sestavení.  
  
 V sadě Visual Studio, nastavte tuto možnost **vlastnosti aplikace** stránky tak, že vyberete **vytvořit aplikaci bez manifestu** možnost **Manifest** rozevíracím seznamu. Další informace najdete v tématu [stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Další informace o vytváření manifestu najdete v tématu [/win32manifest (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
