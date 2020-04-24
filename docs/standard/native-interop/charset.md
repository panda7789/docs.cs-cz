---
title: Charset a zařazování – .NET
description: Přečtěte si, jak různé hodnoty znakové sady můžou změnit způsob, jakým .NET zařazování vašich dat do nativního kódu.
ms.date: 01/18/2019
ms.openlocfilehash: 4be4bd5a968eb5c0d6959a0f378ee1223ed906ed
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706384"
---
# <a name="charsets-and-marshaling"></a>Znakové sady a zařazování

Způsob `char` zařazování hodnot `string` , objektů a `System.Text.StringBuilder` objektů závisí na hodnotě `CharSet` pole v volání nebo ve struktuře. Můžete nastavit `CharSet` hodnotu P/Invoke nastavením <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole při deklaraci volání nespravovaného volání. Pro nastavení `CharSet` pro typ nastavte <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pole v deklaraci třídy nebo struktury. Pokud tato pole atributu nejsou nastavena, je až do kompilátor jazyka, aby bylo možné určit, `CharSet` který z nich se má použít. Jazyk C# a Visual Basic ve <xref:System.Runtime.InteropServices.CharSet.Ansi> výchozím nastavení používat znakovou sadu.

Následující tabulka ukazuje mapování mezi jednotlivými znakové sady a způsob reprezentace znaku nebo řetězce při zařazování pomocí této znakové sady:

| `CharSet`osa | Windows            | .NET Core 2,2 a starší verze v systému UNIX | .NET Core 3,0 a novější a mono v systému UNIX |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char`(výchozí [znaková stránka systému Windows (ANSI)](/windows/win32/intl/code-pages))      | `char`(UTF-8)                    | `char`(UTF-8)                           |
| Kódování Unicode         | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char16_t`(UTF-16)                      |
| Auto            | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char`(UTF-8)                           |

Ujistěte se, že víte, co reprezentace vaší nativní reprezentace očekává při vybírání vaší CharSet.
