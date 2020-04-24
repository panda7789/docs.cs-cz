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
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="439d2-102">Práce s výjimkami spolupráce v nespravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="439d2-102">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="439d2-103">Zprostředkovatel komunikace s výjimkami nespravovaného kódu je podporován pouze na platformách systému Windows.</span><span class="sxs-lookup"><span data-stu-id="439d2-103">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="439d2-104">Problémy s přenositelností vznikají na platformách jiných než Windows.</span><span class="sxs-lookup"><span data-stu-id="439d2-104">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="439d2-105">Vzhledem k tomu, že systém UNIX ABI nemá žádnou definici pro zpracování výjimek, spravovaný kód nemůže znát způsob fungování mechanismů výjimek v rámci pokrývání.</span><span class="sxs-lookup"><span data-stu-id="439d2-105">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="439d2-106">Proto mohou výjimky končit následkem nepředvídatelného chování a selhání.</span><span class="sxs-lookup"><span data-stu-id="439d2-106">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="439d2-107">Chování setjmp/longjmp</span><span class="sxs-lookup"><span data-stu-id="439d2-107">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="439d2-108">Interoperabilita `setjmp` s `longjmp` funkcemi a a C není podporována.</span><span class="sxs-lookup"><span data-stu-id="439d2-108">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="439d2-109">Nemůžete `longjmp` použít k přeskočení spravovaných rámců.</span><span class="sxs-lookup"><span data-stu-id="439d2-109">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="439d2-110">Další informace najdete v [dokumentaci k longjmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).</span><span class="sxs-lookup"><span data-stu-id="439d2-110">For more information, see [longjmp documentation](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="439d2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="439d2-111">See also</span></span>

- [<span data-ttu-id="439d2-112">Výjimky</span><span class="sxs-lookup"><span data-stu-id="439d2-112">Exceptions</span></span>](index.md)
- [<span data-ttu-id="439d2-113">Spolupráce s nativními knihovnami</span><span class="sxs-lookup"><span data-stu-id="439d2-113">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
