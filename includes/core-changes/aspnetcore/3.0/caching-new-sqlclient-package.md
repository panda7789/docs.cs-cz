---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198404"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Ukládání do mezipaměti: Microsoft. Extensions. Caching. SqlServer používá nový balíček SqlClient.

Balíček `Microsoft.Extensions.Caching.SqlServer` použije nový balíček `Microsoft.Data.SqlClient` místo balíčku `System.Data.SqlClient`. Tato změna by mohla způsobit mírné změny v chování. Další informace najdete v tématu [představení nového Microsoft. data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Balíček `Microsoft.Extensions.Caching.SqlServer` použil balíček `System.Data.SqlClient`.

#### <a name="new-behavior"></a>Nové chování

`Microsoft.Extensions.Caching.SqlServer` nyní používá balíček `Microsoft.Data.SqlClient`.

#### <a name="reason-for-change"></a>Důvod změny

`Microsoft.Data.SqlClient` je nový balíček, který je vytvořen z `System.Data.SqlClient`. Je to místo, kde se všechny nové funkce budou dělat hned na.

#### <a name="recommended-action"></a>Doporučená akce

Zákazníci by se neměli muset starat o tuto zásadní změnu, pokud nepoužívali typy vrácené balíčkem `Microsoft.Extensions.Caching.SqlServer` a přetypování do `System.Data.SqlClient` typů. Pokud někdo například přetypování `DbConnection` na [starý typ SqlConnection](xref:System.Data.SqlClient.SqlConnection), museli byste přetypování změnit na nový typ `Microsoft.Data.SqlClient.SqlConnection`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
