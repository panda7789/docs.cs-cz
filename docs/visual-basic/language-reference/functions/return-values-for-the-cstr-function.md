---
title: "Návratové hodnoty pro funkci CStr (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b498c9b1b7916467c96ed2c645c7131192a5e8b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Návratové hodnoty pro funkci CStr (Visual Basic)
Následující tabulka popisuje návratové hodnoty pro `CStr` pro různé datové typy `expression`.  
  
|Pokud `expression` typ|`CStr`Vrátí|  
|-----------------------------|--------------------|  
|[Boolean – datový typ](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Řetězec obsahující "True" nebo "Nepravda".|  
|[Date – datový typ](../../../visual-basic/language-reference/data-types/date-data-type.md)|Řetězec obsahující `Date` hodnotu (datum a čas) ve formátu krátkého data vašeho systému.|  
|[Číselné datové typy](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Řetězec představující číslo.|  
  
## <a name="cstr-and-date"></a>CStr data a času  
 `Date` Typ vždy obsahuje informace o datu a času. Pro účely převod typů, Visual Basic považuje za 1/1/0001 (1. ledna roku 1) *neutrální hodnota* pro datum a 00:00:00 (půlnoc) se má nastavit neutrální hodnota pro dobu. `CStr`nezahrnuje neutrální hodnoty ve výsledném řetězci. Například, pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledkem je "9:30:00: 00"; potlačeno informace o datu. Informace o datu je však stále nachází na původní `Date` hodnotu a je možné obnovit s funkcemi, jako například <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
>  `CStr` Funkce provede jeho převodu na základě aktuální nastavení jazykové verze pro aplikaci. Řetězcová reprezentace čísla v konkrétní jazykové verzi, použijte číslo `ToString(IFormatProvider)` metoda. Například použít <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` k `String`.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Boolean – datový typ](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Date – datový typ](../../../visual-basic/language-reference/data-types/date-data-type.md)
