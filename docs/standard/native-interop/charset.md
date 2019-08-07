---
title: Charset a zařazování – .NET
description: Přečtěte si, jak různé hodnoty znakové sady můžou změnit způsob, jakým .NET zařazování vašich dat do nativního kódu.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: cac71c5d09514dfe1244d16224944e05826edfa9
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817851"
---
# <a name="charsets-and-marshaling"></a>Znakové sady a zařazování

Způsob `char` `string` zařazování`System.Text.StringBuilder` hodnot, objektů a objektů závisí na hodnotě polevvolánínebovestruktuře.`CharSet` Můžete nastavit `CharSet` hodnotu P/Invoke <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> nastavením pole při deklaraci volání nespravovaného volání. `CharSet` Pro nastavení struktury <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> nastavte pole v deklaraci struktury. Pokud tato pole atributu nejsou nastavena, je až do kompilátor jazyka, aby bylo možné určit, `CharSet` který z nich se má použít. C#jazyk VB ve výchozím <xref:System.Runtime.InteropServices.CharSet.Ansi> nastavení používá znakovou sadu.

Následující tabulka ukazuje mapování mezi jednotlivými znakové sady a způsob reprezentace znaku nebo řetězce při zařazování pomocí této znakové sady:

| `CharSet`osa | Windows            | .NET Core 2,2 a starší verze v systému UNIX | .NET Core 3,0 a novější a mono v systému UNIX |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char`(výchozí znaková [stránka systému Windows (ANSI)](/windows/win32/intl/code-pages))      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Kódování Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Auto            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Ujistěte se, že víte, co reprezentace vaší nativní reprezentace očekává při vybírání vaší CharSet.
