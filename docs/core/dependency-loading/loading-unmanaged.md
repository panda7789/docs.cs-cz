---
title: Algoritmus nespravované knihovny pro načítání – .NET Core
description: Popis podrobností algoritmu načítání nespravovaného sestavení v .NET Core
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250038"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>Algoritmus načítání nespravované (nativní) knihovny

Nespravované knihovny se nacházejí a načítají pomocí algoritmu zahrnujícího různé fáze.

Následující algoritmus popisuje, jak jsou načteny nativní knihovny pomocí `PInvoke`.

## <a name="pinvoke-load-library-algorithm"></a>algoritmus knihovny Load `PInvoke`

`PInvoke` používá při pokusu o načtení nespravovaného sestavení následující algoritmus:

1. Určete `active` <xref:System.Runtime.Loader.AssemblyLoadContext>. Pro nespravované knihovny zatížení je `active` AssemblyLoadContext se sestavením, které definuje `PInvoke`.

2. U `active` <xref:System.Runtime.Loader.AssemblyLoadContext> zkuste najít sestavení v pořadí podle priority podle:
    * Kontroluje se její mezipaměť.

    * Volání aktuálního delegáta <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> nastaveného funkcí <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>.

    * Volání funkce <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> na `active` AssemblyLoadContext.

    * Probíhá kontrola mezipaměti instance <xref:System.AppDomain> a spuštění [nespravované (nativní) knihovny zjišťování knihovny](default-probing.md#unmanaged-native-library-probing) .

    * Vyvolává se událost <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> pro `active` AssemblyLoadContext.
