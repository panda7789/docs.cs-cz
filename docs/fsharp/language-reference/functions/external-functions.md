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
# <a name="external-functions"></a>Externí funkce

Toto téma popisuje F# jazykovou podporu pro volání funkcí v nativním kódu.

## <a name="syntax"></a>Syntaxe

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *argumenty* představují argumenty, které jsou dodány `System.Runtime.InteropServices.DllImportAttribute` atributu. První argument je řetězec, který představuje název knihovny DLL, která obsahuje tuto funkci, bez přípony. dll. Další argumenty lze zadat pro libovolnou veřejnou vlastnost `System.Runtime.InteropServices.DllImportAttribute` třídy, jako je například konvence volání.

Předpokládejme, že máte nativní C++ knihovnu DLL, která obsahuje následující exportovanou funkci.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Tuto funkci můžete volat z F# pomocí následujícího kódu.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Interoperabilita s nativním kódem je označována jako *vyvolání platformy* a je funkcí CLR. Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../framework/interop/index.md). Informace v této části se vztahují na F#.

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
