---
title: Algoritmus nespravované knihovny pro načítání – .NET Core
description: Popis podrobností algoritmu načítání nespravovaného sestavení v .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8240cb730180637393e2545f8013d3f1439be719
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017329"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>Algoritmus načítání nespravované (nativní) knihovny

Nespravované knihovny se nacházejí a načítají pomocí algoritmu zahrnujícího různé fáze.

Následující algoritmus popisuje, jak jsou načítány nativní knihovny `PInvoke`pomocí.

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`načíst algoritmus knihovny

`PInvoke`Při pokusu o načtení nespravovaného sestavení používá následující algoritmus:

1. `active` Určete .<xref:System.Runtime.Loader.AssemblyLoadContext> Pro nespravované knihovny `active` zatížení je AssemblyLoadContext volajícím `PInvoke`.

2. `active` Vpřípaděsepokustenajítsestavenív<xref:System.Runtime.Loader.AssemblyLoadContext>pořadí podle priority podle:
    * Kontroluje se její mezipaměť.

    * Volání aktuálního <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegáta nastaveného <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> funkcí.

    * <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> Volání funkce.

    * Kontroluje se <xref:System.AppDomain> mezipaměť instance a spouští nespravovanou [(nativní) logiku zjišťování knihovny](default-probing.md#unmanaged-native-library-probing) .

    * Vyvolává se `active` událost pro AssemblyLoadContext. <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType>

3. Pokud je nespravovaná knihovna nově načtena <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> , událost je vyvolána.
