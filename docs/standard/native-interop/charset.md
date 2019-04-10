---
title: Znakových sad a sběrného systému – .NET
description: Zjistěte, jak různé hodnoty CharSet můžete změnit, jak .NET zařadí data do nativního kódu.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 0b9ea8498b56e6d14770cf57e7e82b9992b1ee50
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299866"
---
# <a name="charsets-and-marshalling"></a>Znakových sad a zařazování

Způsob, jakým `char` hodnoty, `string` objekty, a `System.Text.StringBuilder` objekty jsou zařazeno závisí na hodnotě `CharSet` pole na P/Invoke nebo strukturu. Můžete nastavit `CharSet` P/Invoke tak, že nastavíte <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole při deklarování P/Invoke. Chcete-li nastavit `CharSet` struktury, nastavte <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> na prohlášení vaší struktury. Když tato pole atributu nejsou nastaveny, bude až do kompilátor jazyka pro určení, které `CharSet` používat. C#a použití jazyka Visual Basic <xref:System.Runtime.InteropServices.CharSet.Ansi> znaková sada ve výchozím nastavení.

V následující tabulce jsou uvedeny mapování mezi každou charset a jak znak nebo řetězec představuje při zařazeno pomocí tohoto znaková sada:

| CharSet | Windows            | Unix                                   | Mono v systému Unix        |
|---------|--------------------|----------------------------------------|---------------------|
| Ansi    | `char` (ANSI)      | `char` (ANSI on macOS, UTF-8 on Linux) | `char` (UTF-8)      |
| Kódování Unicode | `wchar_t` (UTF-16) | `char16_t` (UTF-16)                    | `char16_t` (UTF-16) |
| Auto    | `wchar_t` (UTF-16) | `char16_t` (UTF-16)                    | `char` (UTF-8)      |

Ujistěte se, že budete vědět, jaké reprezentace nativní reprezentace očekává, že při výběru vaší znaková sada.
