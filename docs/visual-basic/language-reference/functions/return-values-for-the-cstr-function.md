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
ms.openlocfilehash: cd525ea5a295411e509f3bc37285675d15a8c4f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930053"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Návratové hodnoty pro funkci CStr (Visual Basic)
V následující tabulce jsou popsány návratové hodnoty `CStr` pro různé datové `expression`typy.  
  
|Pokud `expression` typ je|`CStr`Vrátí|  
|-----------------------------|--------------------|  
|[Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Řetězec obsahující "true" nebo "false".|  
|[Datový typ Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|Řetězec obsahující `Date` hodnotu (datum a čas) v krátkém formátu data vašeho systému.|  
|[Číselné datové typy](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Řetězec představující číslo.|  
  
## <a name="cstr-and-date"></a>CStr a datum  
 `Date` Typ vždy obsahuje informace o datu a čase. Pro účely konverze typu Visual Basic považuje 1/1/0001 (1. ledna of year) za *neutrální hodnotu* pro datum a 00:00:00 (půlnoc) jako neutrální hodnotu pro čas. `CStr`nezahrnuje neutrální hodnoty ve výsledném řetězci. Například Pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledkem je "9:30:00 dop.", informace o datu jsou potlačeny. Informace o datu jsou však stále přítomny v původní `Date` hodnotě a lze je obnovit pomocí funkcí, jako je například. <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
  
> [!NOTE]
> `CStr` Funkce provede svůj převod na základě aktuálního nastavení jazykové verze aplikace. Chcete-li získat řetězcové vyjádření čísla v konkrétní jazykové verzi, použijte `ToString(IFormatProvider)` metodu Number. Například použijte <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` na `String`.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Datový typ Date](../../../visual-basic/language-reference/data-types/date-data-type.md)
