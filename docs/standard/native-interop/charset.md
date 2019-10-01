---
title: Charset a zařazování – .NET
description: Přečtěte si, jak různé hodnoty znakové sady můžou změnit způsob, jakým .NET zařazování vašich dat do nativního kódu.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 301fa3d8bd379e76a0e751c3a20d0d8be37d9ac0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700925"
---
# <a name="charsets-and-marshaling"></a>Znakové sady a zařazování

Způsob, jakým jsou zařazování hodnot `char`, objektů `string` a objektů `System.Text.StringBuilder`, závisí na hodnotě pole `CharSet` ve struktuře P/Invoke nebo. Můžete nastavit `CharSet` pro P/Invoke nastavením pole <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> při deklaraci volání metody P/Invoke. Chcete-li nastavit `CharSet` pro typ, nastavte pole <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> v deklaraci třídy nebo struktury. Pokud tato pole atributu nejsou nastavena, je až do kompilátor jazyka, aby bylo možné určit, který `CharSet` použít. C#a VB ve výchozím nastavení používají znakovou sadu <xref:System.Runtime.InteropServices.CharSet.Ansi>.

Následující tabulka ukazuje mapování mezi jednotlivými znakové sady a způsob reprezentace znaku nebo řetězce při zařazování pomocí této znakové sady:

| hodnota `CharSet` | Windows            | .NET Core 2,2 a starší verze v systému UNIX | .NET Core 3,0 a novější a mono v systému UNIX |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (standardní [znaková stránka systému Windows (ANSI)](/windows/win32/intl/code-pages))      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Kódování Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Auto            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Ujistěte se, že víte, co reprezentace vaší nativní reprezentace očekává při vybírání vaší CharSet.
