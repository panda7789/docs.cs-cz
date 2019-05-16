---
title: Externí funkce
description: Další informace o F# jazykovou podporu pro volání funkcí v nativním kódu.
ms.date: 05/16/2016
ms.openlocfilehash: 73e38d8942bfc8ddb3c51d126d7678e84903326b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642050"
---
# <a name="external-functions"></a><span data-ttu-id="cd544-103">Externí funkce</span><span class="sxs-lookup"><span data-stu-id="cd544-103">External Functions</span></span>

<span data-ttu-id="cd544-104">Toto téma popisuje F# jazykovou podporu pro volání funkcí v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="cd544-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd544-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd544-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="cd544-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd544-106">Remarks</span></span>

<span data-ttu-id="cd544-107">V předchozí syntaxi *argumenty* představuje argumenty, které jsou předány `System.Runtime.InteropServices.DllImportAttribute` atribut.</span><span class="sxs-lookup"><span data-stu-id="cd544-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="cd544-108">První argument je řetězec, který představuje název knihovny DLL, která obsahuje tato funkce bez přípony DLL.</span><span class="sxs-lookup"><span data-stu-id="cd544-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="cd544-109">Lze je zadat další argumenty pro všechny veřejné vlastnosti `System.Runtime.InteropServices.DllImportAttribute` třídy, jako je konvence volání.</span><span class="sxs-lookup"><span data-stu-id="cd544-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="cd544-110">Předpokládejme, že máte nativní knihovny DLL jazyka C++, který obsahuje následující exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="cd544-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="cd544-111">Můžete volat tuto funkci z F# pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="cd544-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="cd544-112">Vzájemná funkční spolupráce s nativním kódem se označuje jako *vyvolání platformy* a je funkce modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="cd544-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="cd544-113">Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="cd544-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="cd544-114">Informace v této části se vztahuje na F#.</span><span class="sxs-lookup"><span data-stu-id="cd544-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd544-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd544-115">See also</span></span>

- [<span data-ttu-id="cd544-116">Funkce</span><span class="sxs-lookup"><span data-stu-id="cd544-116">Functions</span></span>](index.md)
