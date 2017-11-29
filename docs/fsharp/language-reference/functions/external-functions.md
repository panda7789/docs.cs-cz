---
title: "Externí funkce (F#)"
description: "Další informace o podpoře jazyka F # pro volání funkcí v nativním kódu."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c26b6124-ceaa-471c-9dc9-861b4dfa332a
ms.openlocfilehash: 4f525b2b750c2ce42230c61aa0e72f957739b206
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="external-functions"></a><span data-ttu-id="f3ee6-104">Externí funkce</span><span class="sxs-lookup"><span data-stu-id="f3ee6-104">External Functions</span></span>

<span data-ttu-id="f3ee6-105">Toto téma popisuje F # jazyková podpora pro volání funkcí v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="f3ee6-105">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3ee6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3ee6-106">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="f3ee6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3ee6-107">Remarks</span></span>

<span data-ttu-id="f3ee6-108">V předchozích syntaxi *argumenty* představuje argumenty, které jsou dodávány `System.Runtime.InteropServices.DllImportAttribute` atribut.</span><span class="sxs-lookup"><span data-stu-id="f3ee6-108">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="f3ee6-109">První argument je řetězec, který představuje název knihovny DLL, která obsahuje tuto funkci, bez příponou .dll.</span><span class="sxs-lookup"><span data-stu-id="f3ee6-109">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="f3ee6-110">Můžete zadat další argumenty pro všechny veřejné vlastnosti `System.Runtime.InteropServices.DllImportAttribute` třídy, například konvence volání.</span><span class="sxs-lookup"><span data-stu-id="f3ee6-110">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="f3ee6-111">Předpokládejme, že máte nativní C++ DLL, která obsahuje následující exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="f3ee6-111">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="f3ee6-112">Tuto funkci lze volat z F # pomocí následující kód.</span><span class="sxs-lookup"><span data-stu-id="f3ee6-112">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="f3ee6-113">Vzájemná funkční spolupráce s nativním kódem se označuje jako *vyvolání platformy* a je funkce modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="f3ee6-113">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="f3ee6-114">Další informace najdete v tématu [spolupráce s nespravovaným kódem](https://msdn.microsoft.com/library/sd10k43k.aspx).</span><span class="sxs-lookup"><span data-stu-id="f3ee6-114">For more information, see [Interoperating with Unmanaged Code](https://msdn.microsoft.com/library/sd10k43k.aspx).</span></span> <span data-ttu-id="f3ee6-115">Informace v této části se vztahuje na F #.</span><span class="sxs-lookup"><span data-stu-id="f3ee6-115">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="f3ee6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3ee6-116">See Also</span></span>

[<span data-ttu-id="f3ee6-117">Funkce</span><span class="sxs-lookup"><span data-stu-id="f3ee6-117">Functions</span></span>](index.md)
