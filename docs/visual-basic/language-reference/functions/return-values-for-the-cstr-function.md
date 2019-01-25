---
title: Návratové hodnoty pro funkci CStr (Visual Basic)
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
ms.openlocfilehash: 22fa31d862259c6dc8607ee44561bc8c18662d88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642815"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Návratové hodnoty pro funkci CStr (Visual Basic)
Následující tabulka popisuje vrácené hodnoty `CStr` pro různé datové typy `expression`.  
  
|Pokud `expression` je typ|`CStr` Vrátí|  
|-----------------------------|--------------------|  
|[Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Řetězec obsahující "True" nebo "Nepravda".|  
|[Datový typ Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|Řetězec obsahující `Date` hodnota (datum a čas) ve formátu krátkého data vašeho systému.|  
|[Číselné datové typy](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Řetězec představující číslo.|  
  
## <a name="cstr-and-date"></a>CStr data a času  
 `Date` Typ vždy obsahuje informace o datu a času. Pro účely převodů, Visual Basic považuje za 1/1/0001 (od 1. ledna roku 1) *neutrální hodnotu* pro datum a 00:00:00 (půlnoc) bude neutrální hodnota pro dobu. `CStr` nezahrnuje neutrální hodnoty ve výsledném řetězci. Například, pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledek je "9:30:00: 00"; informace o datu je potlačeno. Informace o datu je však stále k dispozici v původní `Date` hodnotu a je možné obnovit pomocí funkcí, jako <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
>  `CStr` Funkce provádí její převod na základě nastavení aktuální jazykové verze pro aplikaci. K získání řetězcové vyjádření čísla v konkrétní jazykovou verzi, použijte číslo `ToString(IFormatProvider)` metody. Například použít <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` k `String`.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Datový typ Date](../../../visual-basic/language-reference/data-types/date-data-type.md)
