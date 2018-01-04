---
title: "Sémantika hodnotu Null."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6786c7ea4441b1a753d6f0b4213f40fa64dcb4ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="null-semantics"></a>Sémantika hodnotu Null.
Následující tabulka obsahuje odkazy na různých částí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentace kde `null` (`Nothing` v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) jsou popsány problémy.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Neshody typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|V části "Null sémantiku" v tomto tématu zahrnuje diskuzi o třístavové SQL Boolean versus dvou stavů common language runtime (CLR) <xref:System.Boolean>, skutečné `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) a `null` (C#) a další podobné potíže.|  
|[Převod standardních operátorů dotazů](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|V části "Null sémantiku" v tomto tématu popisuje sémantiku porovnání null v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|[Metody System.String](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|V části "Rozdíly z .NET" v tomto tématu popisuje, jak vrátit 0 z <xref:System.String.LastIndexOf%2A> může znamenat, že řetězec má hodnotu null nebo zda je nalezen pozici 0.|  
|[Nalezení součtu hodnot v číselné posloupnosti](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|Popisuje, jak <xref:System.Linq.Enumerable.Sum%2A> vyhodnocen jako operátor `null` (`Nothing` v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) namísto 0 pro sekvenci, která obsahuje jenom hodnoty Null nebo prázdnou sekvencí.|  
  
## <a name="see-also"></a>Viz také  
 [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
