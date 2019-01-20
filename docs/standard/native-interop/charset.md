---
title: Znakových sad a sběrného systému – .NET
description: Zjistěte, jak různé hodnoty CharSet můžete změnit, jak .NET zařadí data do nativního kódu.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2ff6c485906db481cb5236f83e885ba9fd46450b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416221"
---
# <a name="charsets-and-marshalling"></a>Znakových sad a zařazování

Způsob, jakým `char` hodnoty, `string` objekty, a `System.Text.StringBuilder` objekty jsou zařazeno závisí na hodnotě `CharSet` pole na P/Invoke nebo strukturu. Můžete nastavit `CharSet` P/Invoke tak, že nastavíte <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole při deklarování P/Invoke. Chcete-li nastavit `CharSet` struktury, nastavte <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> na prohlášení vaší struktury. Když tato pole atributu nejsou nastaveny, bude až do kompilátor jazyka pro určení, které `CharSet` používat. C#používá <xref:System.Runtime.InteropServices.CharSet.Ansi> znaková sada ve výchozím nastavení.

V následující tabulce jsou uvedeny mapování mezi každou charset a jak znak nebo řetězec představuje při zařazeno pomocí tohoto znaková sada:

| CharSet | Windows | Unix | Mono v systému Unix |
|---------|---------|-------|-------|
| Ansi    | `char` (ANSI)  | `char` (ANSI on macOS, UTF-8 on Linux) | `char` (UTF-8) |
| Kódování Unicode | `wchar_t` (UTF-16) | `char16_t` (UTF-16) | `char16_t` (UTF-16) |
| Auto | `wchar_t` (UTF-16) | `char16_t` (UTF-16) | `char` (UTF-8) |

Ujistěte se, že budete vědět, jaké reprezentace nativní reprezentace očekává, že při výběru vaší znaková sada.
