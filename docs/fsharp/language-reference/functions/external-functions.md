---
title: Externí funkce
description: Přečtěte si F# o podpoře jazyků pro volání funkcí v nativním kódu.
ms.date: 05/16/2016
ms.openlocfilehash: 3c8edaba25e07b6ca2c44a58c4b55dc98a13b4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968733"
---
# <a name="external-functions"></a><span data-ttu-id="1539b-103">Externí funkce</span><span class="sxs-lookup"><span data-stu-id="1539b-103">External Functions</span></span>

<span data-ttu-id="1539b-104">Toto téma popisuje F# jazykovou podporu pro volání funkcí v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="1539b-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="1539b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1539b-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="1539b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1539b-106">Remarks</span></span>

<span data-ttu-id="1539b-107">V předchozí syntaxi *argumenty* představují argumenty, které jsou dodány `System.Runtime.InteropServices.DllImportAttribute` atributu.</span><span class="sxs-lookup"><span data-stu-id="1539b-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="1539b-108">První argument je řetězec, který představuje název knihovny DLL, která obsahuje tuto funkci, bez přípony. dll.</span><span class="sxs-lookup"><span data-stu-id="1539b-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="1539b-109">Další argumenty lze zadat pro libovolnou veřejnou vlastnost `System.Runtime.InteropServices.DllImportAttribute` třídy, jako je například konvence volání.</span><span class="sxs-lookup"><span data-stu-id="1539b-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="1539b-110">Předpokládejme, že máte nativní C++ knihovnu DLL, která obsahuje následující exportovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="1539b-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="1539b-111">Tuto funkci můžete volat z F# pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="1539b-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="1539b-112">Interoperabilita s nativním kódem je označována jako *vyvolání platformy* a je funkcí CLR.</span><span class="sxs-lookup"><span data-stu-id="1539b-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="1539b-113">Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="1539b-113">For more information, see [Interoperating with Unmanaged Code](../../../framework/interop/index.md).</span></span> <span data-ttu-id="1539b-114">Informace v této části se vztahují na F#.</span><span class="sxs-lookup"><span data-stu-id="1539b-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="1539b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1539b-115">See also</span></span>

- [<span data-ttu-id="1539b-116">Funkce</span><span class="sxs-lookup"><span data-stu-id="1539b-116">Functions</span></span>](index.md)
