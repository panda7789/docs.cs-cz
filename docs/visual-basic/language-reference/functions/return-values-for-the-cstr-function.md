---
title: Návratové hodnoty pro funkci CStr
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 6039ba3f6bd1c364db818807604ee0851bc23d50
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406381"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Návratové hodnoty pro funkci CStr (Visual Basic)
V následující tabulce jsou popsány návratové hodnoty pro `CStr` různé datové typy `expression` .  
  
|Pokud `expression` typ je|`CStr`Vrátí|  
|-----------------------------|--------------------|  
|[Boolean – datový typ](../data-types/boolean-data-type.md)|Řetězec obsahující "true" nebo "false".|  
|[Date – datový typ](../data-types/date-data-type.md)|Řetězec obsahující `Date` hodnotu (datum a čas) v krátkém formátu data vašeho systému.|  
|[Číselné datové typy](../../programming-guide/language-features/data-types/numeric-data-types.md)|Řetězec představující číslo.|  
  
## <a name="cstr-and-date"></a>CStr a datum  
 `Date`Typ vždy obsahuje informace o datu a čase. Pro účely konverze typu Visual Basic považuje 1/1/0001 (1. ledna of year) za *neutrální hodnotu* pro datum a 00:00:00 (půlnoc) jako neutrální hodnotu pro čas. `CStr`nezahrnuje neutrální hodnoty ve výsledném řetězci. Například Pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledkem je "9:30:00 dop.", informace o datu jsou potlačeny. Informace o datu jsou však stále přítomny v původní `Date` hodnotě a lze je obnovit pomocí funkcí, jako je například <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> .  
  
> [!NOTE]
> `CStr`Funkce provede svůj převod na základě aktuálního nastavení jazykové verze aplikace. Chcete-li získat řetězcové vyjádření čísla v konkrétní jazykové verzi, použijte `ToString(IFormatProvider)` metodu Number. Například použijte <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` na `String` .  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Funkce pro převod typů](type-conversion-functions.md)
- [Boolean – datový typ](../data-types/boolean-data-type.md)
- [Date – datový typ](../data-types/date-data-type.md)
