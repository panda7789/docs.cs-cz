---
title: Globalizace – průlomové změny
description: Obsahuje seznam nejnovějších změn v globalizaci v .NET Core.
ms.date: 04/07/2020
ms.openlocfilehash: 0c3367cb3515c6f473f53be6062b54f2e836b8c5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702291"
---
# <a name="globalization-breaking-changes"></a>Globalizace – průlomové změny

Na této stránce jsou popsány následující přerušující se změny:

| Zásadní změna | Představená verze |
| - | :-: |
| [Rozhraní API globalizace používají knihovny ICU ve Windows](#globalization-apis-use-icu-libraries-on-windows) | 5.0 |
| [StringInfo a TextElementEnumerator jsou nyní kompatibilní s UAX29](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | 5.0 |
| [Národní prostředí jazyka C se mapuje na neutrální národní prostředí.](#c-locale-maps-to-the-invariant-locale) | 3.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
