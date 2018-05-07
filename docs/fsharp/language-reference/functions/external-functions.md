---
title: Externí funkce (F#)
description: 'Další informace o podpoře jazyka F # pro volání funkcí v nativním kódu.'
ms.date: 05/16/2016
ms.openlocfilehash: 398697c5e0deab7f8d81ec5198ab1918bd865e13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="external-functions"></a>Externí funkce

Toto téma popisuje F # jazyková podpora pro volání funkcí v nativním kódu.

## <a name="syntax"></a>Syntaxe

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Poznámky

V předchozích syntaxi *argumenty* představuje argumenty, které jsou dodávány `System.Runtime.InteropServices.DllImportAttribute` atribut. První argument je řetězec, který představuje název knihovny DLL, která obsahuje tuto funkci, bez příponou .dll. Můžete zadat další argumenty pro všechny veřejné vlastnosti `System.Runtime.InteropServices.DllImportAttribute` třídy, například konvence volání.

Předpokládejme, že máte nativní C++ DLL, která obsahuje následující exportované funkce.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Tuto funkci lze volat z F # pomocí následující kód.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Vzájemná funkční spolupráce s nativním kódem se označuje jako *vyvolání platformy* a je funkce modulu CLR. Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md). Informace v této části se vztahuje na F #.


## <a name="see-also"></a>Viz také

[Funkce](index.md)
