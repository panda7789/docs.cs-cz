---
title: -nowin32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: df05ff6caeae2fb2db6a8d7c8fec1b81774a9fa4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005387"
---
# <a name="-nowin32manifest-visual-basic"></a>-nowin32manifest (Visual Basic)
Instruuje kompilátor, aby nevložil žádný manifest aplikace do spustitelného souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud použijete tuto možnost, bude se aplikace vztahovat k virtualizaci v systému Windows Vista, pokud neposkytnete manifest aplikace v souboru prostředků Win32 nebo během pozdějšího kroku sestavení. Další informace o virtualizaci najdete v tématu [nasazení ClickOnce v systému Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Další informace o vytváření manifestu naleznete v tématu [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
