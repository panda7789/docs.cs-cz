---
title: Metody System.String
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 569010c36296e18487eb52527d3df0cc0b97cf06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618115"
---
# <a name="systemstring-methods"></a>Metody System.String
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje následující <xref:System.String> metody.  
  
## <a name="unsupported-systemstring-methods-in-general"></a>Obecně nepodporované metody System.String  
 Nepodporovaná <xref:System.String> v obecné metody:  
  
-   Zohledňující jazykovou verzi přetížení (metody, které přebírají `CultureInfo`  /  `StringComparison`  /  `IFormatProvider`).  
  
-   Metody, které trvat nebo vytvářet `char` pole.  
  
## <a name="unsupported-systemstring-static-methods"></a>Nepodporovaná System.String statické metody  
  
|Nepodporovaná System.String statické metody|  
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
  
## <a name="unsupported-systemstring-non-static-methods"></a>Nepodporovaná System.String nestatických metod  
  
|Nepodporovaná System.String nestatických metod|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a>Rozdíl oproti .NET  
  
-   Dotazy nespadá kolací systému SQL Server, které může být výsledkem bude na serveru a proto bude poskytovat Porovnání zohledňující jazykovou verzi, velká a malá písmena ve výchozím nastavení. Toto chování se liší od výchozí malá a velká písmena sémantiku rozhraní .NET Framework.  
  
-   Když `LastIndexOf` vrátí hodnotu 0, řetězec je `NULL` nebo nalezený pozice je 0.  
  
-   Může vrátit neočekávané výsledky ze zřetězení nebo jiné operace na řetězce pevné délky (`CHAR`, `NCHAR`), protože tyto typy mají automaticky odsazení použijí v databázi.  
  
-   Protože mnoho metod, jako `Replace`, `ToLower`, `ToUpper`a indexeru znaků, obsahovat žádný platný překlad pro `TEXT` nebo `NTEXT` sloupce a XML, `SqlExceptions` dojít, pokud obvykle přeložit. Toto chování se považuje za přijatelné pro tyto typy. Nicméně všechny operace s řetězci musí odpovídat common language runtime (CLR) Sémantika pro `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, a `NVARCHAR(max)`.  
  
## <a name="see-also"></a>Viz také:
- [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
