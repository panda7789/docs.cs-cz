---
ms.openlocfilehash: 687118157020ede200f97a0125c4740a06bf4b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620014"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Různé zpracování výjimek pro metody ObjectContext. CreateDatabase a DbProviderServices. CreateDatabase

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5, pokud se vytvoření databáze nezdaří, <code>CreateDatabase</code> metody se pokusí odstranit prázdnou databázi. Pokud je tato operace úspěšná, <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> bude rozšířena původní (místo toho <xref:System.InvalidOperationException?displayProperty=fullName> , který byl vždy vyvolán v .NET Framework 4,0).

#### <a name="suggestion"></a>Návrh

Při zachycení <xref:System.InvalidOperationException?displayProperty=fullName> při spuštění <xref:System.Data.Objects.ObjectContext.CreateDatabase> nebo <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)> SQLExceptions by nyní mělo být zachyceno také.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
