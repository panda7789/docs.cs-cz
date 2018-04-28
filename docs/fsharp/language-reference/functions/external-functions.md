---
title: Externí funkce (F#)
description: 'Další informace o podpoře jazyka F # pro volání funkcí v nativním kódu.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 28e74258d91ff2d9742caa7a6c06f515cd987c0a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="external-functions"></a><span data-ttu-id="8a6c5-103">Externí funkce</span><span class="sxs-lookup"><span data-stu-id="8a6c5-103">External Functions</span></span>

<span data-ttu-id="8a6c5-104">Toto téma popisuje F # jazyková podpora pro volání funkcí v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="8a6c5-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a6c5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a6c5-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="8a6c5-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a6c5-106">Remarks</span></span>

<span data-ttu-id="8a6c5-107">V předchozích syntaxi *argumenty* představuje argumenty, které jsou dodávány `System.Runtime.InteropServices.DllImportAttribute` atribut.</span><span class="sxs-lookup"><span data-stu-id="8a6c5-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="8a6c5-108">První argument je řetězec, který představuje název knihovny DLL, která obsahuje tuto funkci, bez příponou .dll.</span><span class="sxs-lookup"><span data-stu-id="8a6c5-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="8a6c5-109">Můžete zadat další argumenty pro všechny veřejné vlastnosti `System.Runtime.InteropServices.DllImportAttribute` třídy, například konvence volání.</span><span class="sxs-lookup"><span data-stu-id="8a6c5-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="8a6c5-110">Předpokládejme, že máte nativní C++ DLL, která obsahuje následující exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="8a6c5-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="8a6c5-111">Tuto funkci lze volat z F # pomocí následující kód.</span><span class="sxs-lookup"><span data-stu-id="8a6c5-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="8a6c5-112">Vzájemná funkční spolupráce s nativním kódem se označuje jako *vyvolání platformy* a je funkce modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="8a6c5-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="8a6c5-113">Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="8a6c5-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="8a6c5-114">Informace v této části se vztahuje na F #.</span><span class="sxs-lookup"><span data-stu-id="8a6c5-114">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="8a6c5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a6c5-115">See Also</span></span>

[<span data-ttu-id="8a6c5-116">Funkce</span><span class="sxs-lookup"><span data-stu-id="8a6c5-116">Functions</span></span>](index.md)
