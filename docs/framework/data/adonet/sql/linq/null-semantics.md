---
title: Sémantika s hodnotou null
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: d0b18c0a699840d11f5e4add05147672f9bb69e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792977"
---
# <a name="null-semantics"></a>Sémantika s hodnotou null
Následující tabulka obsahuje odkazy na různé části [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentace, kde `null` jsou popsány problémy (`Nothing` v Visual Basic).  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Neshody typů SQL a CLR](sql-clr-type-mismatches.md)|Oddíl "sémantika hodnoty null" v tomto tématu obsahuje diskuzi o třech stavech SQL logických versus dvou stavech modulu CLR (Common Language Runtime <xref:System.Boolean>), literálu `Nothing` (Visual Basic) `null` aC#() a dalších podobných Chyba.|  
|[Převod standardních operátorů dotazů](standard-query-operator-translation.md)|Oddíl "sémantika hodnoty null" v tomto tématu popisuje sémantiku porovnání s hodnotou [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]null v.|  
|[Metody System.String](system-string-methods.md)|Část rozdíly od .NET tohoto tématu popisuje, jak vrácení 0 z <xref:System.String.LastIndexOf%2A> může znamenat, že řetězec je null nebo že nalezená pozice je 0.|  
|[Nalezení součtu hodnot v číselné posloupnosti](compute-the-sum-of-values-in-a-numeric-sequence.md)|Popisuje, jak <xref:System.Linq.Enumerable.Sum%2A> se operátor vyhodnocuje `null` (`Nothing` v Visual Basic) místo 0 pro sekvenci, která obsahuje pouze hodnoty null nebo prázdné sekvence.|  
  
## <a name="see-also"></a>Viz také:

- [Datové typy a funkce](data-types-and-functions.md)
