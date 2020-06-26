---
title: Charset a zařazování – .NET
description: Přečtěte si, jak různé hodnoty znakové sady můžou změnit způsob, jakým .NET zařazování vašich dat do nativního kódu.
ms.date: 01/18/2019
ms.openlocfilehash: 39566593aa38bacfa41b44a8af8cc2dfb294d766
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416106"
---
# <a name="charsets-and-marshaling"></a>Znakové sady a zařazování

Způsob `char` `string` zařazování hodnot, objektů a `System.Text.StringBuilder` objektů závisí na hodnotě `CharSet` pole v volání nebo ve struktuře. Můžete nastavit hodnotu `CharSet` P/Invoke nastavením <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole při deklaraci volání nespravovaného volání. Pro nastavení `CharSet` pro typ nastavte <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pole v deklaraci třídy nebo struktury. Pokud tato pole atributu nejsou nastavena, je až do kompilátor jazyka, aby bylo možné určit, který z nich `CharSet` se má použít. Jazyk C# a Visual Basic <xref:System.Runtime.InteropServices.CharSet.Ansi> ve výchozím nastavení používat znakovou sadu.

Následující tabulka ukazuje mapování mezi jednotlivými znakové sady a způsob reprezentace znaku nebo řetězce při zařazování pomocí této znakové sady:

| `CharSet`osa | Windows            | .NET Core 2,2 a starší verze v systému UNIX | .NET Core 3,0 a novější a mono v systému UNIX |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| `Ansi`          | `char`(výchozí [znaková stránka systému Windows (ANSI)](/windows/win32/intl/code-pages))      | `char`(UTF-8)                    | `char`(UTF-8)                           |
| `Unicode`       | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char16_t`(UTF-16)                      |
| `Auto`          | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char`(UTF-8)                           |

Ujistěte se, že víte, co reprezentace vaší nativní reprezentace očekává při vybírání vaší CharSet.
