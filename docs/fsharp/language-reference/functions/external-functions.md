---
title: Externí funkce (F#)
description: 'Další informace o podpoře jazyka F # pro volání funkcí v nativním kódu.'
ms.date: 05/16/2016
ms.openlocfilehash: db0d3362d867b07b333951f3380c6735ff471d5e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45973102"
---
# <a name="external-functions"></a>Externí funkce

Toto téma popisuje podpora jazyka F # pro volání funkcí v nativním kódu.

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

Pomocí následujícího kódu můžete volat tuto funkci z jazyka F #.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Vzájemná funkční spolupráce s nativním kódem se označuje jako *vyvolání platformy* a je funkce modulu CLR. Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md). Informace v této části platí pro F #.

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
