---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198404"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Ukládání do mezipaměti: Microsoft.Extensions.Caching.SqlServer používá nový balíček SqlClient

Balíček `Microsoft.Extensions.Caching.SqlServer` bude používat `Microsoft.Data.SqlClient` nový `System.Data.SqlClient` balíček namísto balíčku. Tato změna může způsobit mírné změny chování lámání. Další informace naleznete [v tématu Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Balíček `Microsoft.Extensions.Caching.SqlServer` použil `System.Data.SqlClient` balíček.

#### <a name="new-behavior"></a>Nové chování

`Microsoft.Extensions.Caching.SqlServer`nyní používá `Microsoft.Data.SqlClient` balíček.

#### <a name="reason-for-change"></a>Důvod změny

`Microsoft.Data.SqlClient`je nový balíček, který `System.Data.SqlClient`je postaven mimo . To je místo, kde všechny nové funkce práce bude provedeno od nynějška.

#### <a name="recommended-action"></a>Doporučená akce

Zákazníci by se neměli obávat této narušující změny, pokud nepoužívali typy vrácené `Microsoft.Extensions.Caching.SqlServer` balíčkem a přetypovali je na `System.Data.SqlClient` typy. Například pokud někdo byl `DbConnection` přetypování na [starý typ SqlConnection](xref:System.Data.SqlClient.SqlConnection), budou `Microsoft.Data.SqlClient.SqlConnection` muset změnit přetypování na nový typ.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
