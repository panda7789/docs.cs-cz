---
title: Charset a zařazování – .NET
description: Přečtěte si, jak různé hodnoty znakové sady můžou změnit způsob, jakým .NET zařazování vašich dat do nativního kódu.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: a29d53f8e422da1a78e131110972d83987c5464a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337925"
---
# <a name="charsets-and-marshaling"></a>Znakové sady a zařazování

Způsob, jakým `char` jsou zařazování hodnot, `string` objektů a objektů `System.Text.StringBuilder`, závisí na hodnotě `CharSet` pole ve struktuře P/Invoke nebo. Můžete nastavit `CharSet` volání nespravovaného systému nastavením pole <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> při deklaraci volání metody P/Invoke. Chcete-li nastavit `CharSet` pro určitý typ, nastavte pole <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> v deklaraci třídy nebo struktury. Pokud tato pole atributu nejsou nastavena, je až do kompilátor jazyka, aby bylo možné určit, který `CharSet` použít. C#ve výchozím nastavení Visual Basic použít znakovou sadu <xref:System.Runtime.InteropServices.CharSet.Ansi>.

Následující tabulka ukazuje mapování mezi jednotlivými znakové sady a způsob reprezentace znaku nebo řetězce při zařazování pomocí této znakové sady:

| hodnota `CharSet` | Windows            | .NET Core 2,2 a starší verze v systému UNIX | .NET Core 3,0 a novější a mono v systému UNIX |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (standardní [znaková stránka systému Windows (ANSI)](/windows/win32/intl/code-pages))      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Kódování Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Autom.            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Ujistěte se, že víte, co reprezentace vaší nativní reprezentace očekává při vybírání vaší CharSet.
