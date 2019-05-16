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
# <a name="external-functions"></a>Externí funkce

Toto téma popisuje F# jazykovou podporu pro volání funkcí v nativním kódu.

## <a name="syntax"></a>Syntaxe

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *argumenty* představuje argumenty, které jsou předány `System.Runtime.InteropServices.DllImportAttribute` atribut. První argument je řetězec, který představuje název knihovny DLL, která obsahuje tato funkce bez přípony DLL. Lze je zadat další argumenty pro všechny veřejné vlastnosti `System.Runtime.InteropServices.DllImportAttribute` třídy, jako je konvence volání.

Předpokládejme, že máte nativní knihovny DLL jazyka C++, který obsahuje následující exportované funkce.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Můžete volat tuto funkci z F# pomocí následujícího kódu.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Vzájemná funkční spolupráce s nativním kódem se označuje jako *vyvolání platformy* a je funkce modulu CLR. Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md). Informace v této části se vztahuje na F#.

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
