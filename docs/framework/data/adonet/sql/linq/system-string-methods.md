---
title: System.String metody
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d33e99c0fb184413c989900b652ce7bb5b5d67eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemstring-methods"></a>System.String metody
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje následující <xref:System.String> metody.  
  
## <a name="unsupported-systemstring-methods-in-general"></a>Nepodporované metody System.String obecně  
 Nepodporované <xref:System.String> metody v obecné:  
  
-   Podporující jazykové verze přetížení (metod, které berou `CultureInfo`  /  `StringComparison`  /  `IFormatProvider`).  
  
-   Metody, které trvat nebo vytvořit `char` pole.  
  
## <a name="unsupported-systemstring-static-methods"></a>Nepodporované System.String statické metody  
  
|Nepodporované System.String statické metody|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a>Nepodporované System.String nestatické metody  
  
|Nepodporované System.String nestatické metody|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a>Rozdíl oproti rozhraní .NET  
  
-   Dotazy nespadá kolace systému SQL Server, které může být výsledkem bude na serveru a proto bude poskytovat zohledňující jazykovou verzi, bez rozlišování velikosti písmen porovnání ve výchozím nastavení. Toto chování se liší od výchozí, malá a velká písmena sémantiku rozhraní .NET Framework.  
  
-   Když `LastIndexOf` vrátí hodnotu 0, buď řetězec je `NULL` nebo se nachází pozice 0.  
  
-   Neočekávané výsledky může být vrácena z zřetězení nebo jiné operace v řetězce pevné délky (`CHAR`, `NCHAR`), protože tyto typy automaticky mají odsazení použité v databázi.  
  
-   Protože mnoho způsobů, například `Replace`, `ToLower`, `ToUpper`a znak indexeru, mít žádné platné překlad pro `TEXT` nebo `NTEXT` sloupce a XML, `SqlExceptions` dojít, pokud přeložit normálně. Toto chování se považuje za přijatelné pro tyto typy. Ale musí být všechny operace s řetězci stejný běžné sémantiku language runtime (CLR) pro `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, a `NVARCHAR(max)`.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
