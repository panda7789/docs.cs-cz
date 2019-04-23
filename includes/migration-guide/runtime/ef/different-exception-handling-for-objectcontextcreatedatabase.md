---
ms.openlocfilehash: 33ad1c044001e0a8d09708cc7a1f06e05cb307de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803691"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Zpracování metody ObjectContext.CreateDatabase a DbProviderServices.CreateDatabase různých výjimek

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, pokud se vytváření databáze nezdaří, <code>CreateDatabase</code> metody se pokusí zrušit prázdnou databázi. Pokud operace proběhne úspěšně, původní <xref:System.Data.SqlClient.SqlException?displayProperty=name> se rozšíří (místo <xref:System.InvalidOperationException?displayProperty=name> , která byla vždy vyvolána v rozhraní .NET Framework 4.0)|
|Doporučení|Při zachytávání <xref:System.InvalidOperationException?displayProperty=name> při provádění <xref:System.Data.Objects.ObjectContext.CreateDatabase> nebo <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions by měl nyní také být zachycena.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
