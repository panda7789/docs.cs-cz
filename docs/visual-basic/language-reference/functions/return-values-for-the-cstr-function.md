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
ms.openlocfilehash: 5312734633eea12aacd7e61afba616d31e06cd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Návratové hodnoty pro funkci CStr (Visual Basic)
Následující tabulka popisuje návratové hodnoty pro `CStr` pro různé datové typy `expression`.  
  
|Pokud `expression` typ|`CStr` Vrátí|  
|-----------------------------|--------------------|  
|[Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Řetězec obsahující "True" nebo "Nepravda".|  
|[Datový typ Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|Řetězec obsahující `Date` hodnotu (datum a čas) ve formátu krátkého data vašeho systému.|  
|[Číselné datové typy](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Řetězec představující číslo.|  
  
## <a name="cstr-and-date"></a>CStr data a času  
 `Date` Typ vždy obsahuje informace o datu a času. Pro účely převod typů, Visual Basic považuje za 1/1/0001 (1. ledna roku 1) *neutrální hodnota* pro datum a 00:00:00 (půlnoc) se má nastavit neutrální hodnota pro dobu. `CStr` nezahrnuje neutrální hodnoty ve výsledném řetězci. Například, pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledkem je "9:30:00: 00"; potlačeno informace o datu. Informace o datu je však stále nachází na původní `Date` hodnotu a je možné obnovit s funkcemi, jako například <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
>  `CStr` Funkce provede jeho převodu na základě aktuální nastavení jazykové verze pro aplikaci. Řetězcová reprezentace čísla v konkrétní jazykové verzi, použijte číslo `ToString(IFormatProvider)` metoda. Například použít <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` k `String`.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Datový typ Date](../../../visual-basic/language-reference/data-types/date-data-type.md)
