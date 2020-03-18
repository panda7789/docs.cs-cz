---
title: Algoritmus načítání nespravované knihovny - .NET Core
description: Popis podrobností o algoritmu načítání nespravovaného sestavení v rozhraní .NET Core
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72250038"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>Algoritmus načítání nespravované (nativní) knihovny

Nespravované knihovny jsou umístěny a načteny s algoritmem zahrnujícím různé fáze.

Následující algoritmus popisuje, jak jsou `PInvoke`nativní knihovny načteny prostřednictvím aplikace .

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`algoritmus knihovny zatížení

`PInvoke`Při pokusu o načtení nespravovaného sestavení používá následující algoritmus:

1. Určete `active` <xref:System.Runtime.Loader.AssemblyLoadContext>. Pro nespravovanou knihovnu `active` zatížení assemblyloadcontext je ten s `PInvoke`sestavením, které definuje .

2. V `active` <xref:System.Runtime.Loader.AssemblyLoadContext>oblasti se pokuste najít sestavení v pořadí podle priority:
    * Kontroluji jeho mezipaměť.

    * Volání aktuálního <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegáta <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> nastaveného funkcí.

    * Volání <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> funkce na `active` AssemblyLoadContext.

    * Kontrola mezipaměti <xref:System.AppDomain> instance a spuštění logiky zjišťování [nespravované (nativní) knihovny.](default-probing.md#unmanaged-native-library-probing)

    * Vyvolání <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> události `active` pro AssemblyLoadContext.
