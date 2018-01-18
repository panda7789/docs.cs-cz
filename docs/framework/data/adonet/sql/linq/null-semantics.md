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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8d32f73c8c2095c23ec164ad40fd1ab27ef1153a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
