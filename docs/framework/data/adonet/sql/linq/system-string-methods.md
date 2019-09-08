---
title: Metody System.String
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 583c0d58562c1605f24b61489d481e19248ebed4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792503"
---
# <a name="systemstring-methods"></a>Metody System.String
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje následující <xref:System.String> metody.  
  
## <a name="unsupported-systemstring-methods-in-general"></a>Nepodporované metody System. String obecně  
 Obecně <xref:System.String> nepodporované metody:  
  
- Přetížení zohledňující jazykovou verzi `CultureInfo`(metody, které přijímají  /  `StringComparison`  /  `IFormatProvider`).  
  
- Metody, které přijímají nebo `char` vytvoří pole.  
  
## <a name="unsupported-systemstring-static-methods"></a>Statické metody System. String nejsou podporovány.  
  
|Statické metody System. String nejsou podporovány.|  
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
  
## <a name="unsupported-systemstring-non-static-methods"></a>Nepodporované metody System. String nestatického typu  
  
|Nepodporované metody System. String nestatického typu|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a>Rozdíly od .NET  
  
- Dotazy neumožňují SQL Server kolace, které mohou být v platnosti na serveru, a proto budou ve výchozím nastavení zajišťovat porovnávání bez rozlišení velkých a malých písmen. Toto chování se liší od výchozí sémantiky a rozlišující velká a malá písmena .NET Framework.  
  
- Když `LastIndexOf` funkce vrátí hodnotu 0, buď je `NULL` řetězec, nebo nalezená pozice je 0.  
  
- Neočekávané výsledky mohou být vráceny z zřetězení nebo jiných operací na řetězce s pevnou délkou `NCHAR`(`CHAR`,), protože tyto typy mají automaticky v databázi použitu výplň.  
  
- Vzhledem k tomu, že mnoho `Replace`metod `ToLower`, `ToUpper`jako je,, a indexer znaků, nemá žádný platný překlad `TEXT` pro `NTEXT` sloupce nebo sloupce jazyka `SqlExceptions` XML, dochází-li k překladu normálně. Toto chování je považováno za přijatelné pro tyto typy. Všechny operace s řetězci musí však odpovídat sémantikě modulu CLR (Common Language Runtime) `VARCHAR`pro `NVARCHAR`, `VARCHAR(max)`, a `NVARCHAR(max)`.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy a funkce](data-types-and-functions.md)
