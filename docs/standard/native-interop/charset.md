---
title: Znakových sad a zařazování – .NET
description: Zjistěte, jak různé hodnoty CharSet můžete změnit, jak .NET zařadí data do nativního kódu.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: c50c58ad639b1efb29c13e5124fe3c32e8af96fc
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063338"
---
# <a name="charsets-and-marshaling"></a>Znakových sad a zařazování

Způsob, jakým `char` hodnoty, `string` objekty, a `System.Text.StringBuilder` objekty, které jsou zařazeny závisí na hodnotě `CharSet` pole na P/Invoke nebo strukturu. Můžete nastavit `CharSet` P/Invoke tak, že nastavíte <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole při deklarování P/Invoke. Chcete-li nastavit `CharSet` struktury, nastavte <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> na prohlášení vaší struktury. Když tato pole atributu nejsou nastaveny, bude až do kompilátor jazyka pro určení, které `CharSet` používat. C#a použití jazyka Visual Basic <xref:System.Runtime.InteropServices.CharSet.Ansi> znaková sada ve výchozím nastavení.

V následující tabulce jsou uvedeny mapování mezi každou charset a jak znak nebo řetězec představuje při zařazení pomocí tohoto znaková sada:

| `CharSet` Hodnota | Windows            | .NET core 2.2 a dříve v systému Unix | .NET core 3.0 a novější a Mono v systému Unix |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (ANSI)      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Kódování Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Auto            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Ujistěte se, že budete vědět, jaké reprezentace nativní reprezentace očekává, že při výběru vaší znaková sada.
