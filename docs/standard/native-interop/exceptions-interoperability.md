---
title: Interoperabilita výjimek
ms.date: 01/16/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 2aff71e97e1be0dbb584f4fe43c322cea86d2480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795173"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a>Práce s výjimkami spolupráce v nespravovaném kódu

Zprostředkovatel komunikace s výjimkami nespravovaného kódu je podporován pouze na platformách systému Windows. Problémy s přenositelností vznikají na platformách jiných než Windows. Vzhledem k tomu, že systém UNIX ABI nemá žádnou definici pro zpracování výjimek, spravovaný kód nemůže znát způsob fungování mechanismů výjimek v rámci pokrývání. Proto mohou výjimky končit následkem nepředvídatelného chování a selhání.

## <a name="setjmplongjmp-behaviors"></a>Chování setjmp/longjmp

Spolupráce s funkcemi `setjmp` a `longjmp` C se nepodporuje. Nemůžete použít `longjmp` k přeskočení spravovaných rámců.

Další informace najdete v [dokumentaci k longjmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
- [Spolupráce s nativními knihovnami](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
