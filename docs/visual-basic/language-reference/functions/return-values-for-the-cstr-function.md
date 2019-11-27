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
ms.openlocfilehash: 4a40777c7290ec6d8c0d032f2edca5d889e20f04
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349986"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Návratové hodnoty pro funkci CStr (Visual Basic)
Následující tabulka popisuje návratové hodnoty pro `CStr` pro různé datové typy `expression`.  
  
|Pokud je `expression` typ|`CStr` vrátí|  
|-----------------------------|--------------------|  
|[Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Řetězec obsahující "true" nebo "false".|  
|[Datový typ Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|Řetězec obsahující `Date` hodnotu (datum a čas) v krátkém formátu data systému.|  
|[Číselné datové typy](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Řetězec představující číslo.|  
  
## <a name="cstr-and-date"></a>CStr a datum  
 Typ `Date` vždy obsahuje informace o datu a čase. Pro účely konverze typu Visual Basic považuje 1/1/0001 (1. ledna of year) za *neutrální hodnotu* pro datum a 00:00:00 (půlnoc) jako neutrální hodnotu pro čas. `CStr` nezahrnuje neutrální hodnoty ve výsledném řetězci. Pokud například převedete `#January 1, 0001 9:30:00#` na řetězec, výsledek je "9:30:00 dop."; informace o datu jsou potlačeny. Informace o datu jsou však stále přítomny v původní `Date` hodnotě a lze je obnovit pomocí funkcí, jako je například <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
> Funkce `CStr` provádí svůj převod na základě aktuálního nastavení jazykové verze aplikace. Chcete-li získat řetězcové vyjádření čísla v konkrétní jazykové verzi, použijte metodu `ToString(IFormatProvider)` číslo. Například použijte <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` na `String`.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Datový typ Date](../../../visual-basic/language-reference/data-types/date-data-type.md)
