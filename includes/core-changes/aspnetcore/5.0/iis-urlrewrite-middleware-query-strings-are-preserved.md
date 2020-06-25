---
ms.openlocfilehash: 29908ed916690e67db3cc5d72ebe1b1c6aea45c6
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325216"
---
### <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a>IIS: UrlRewrite řetězce dotazů middleware jsou zachovány.

UrlRewrite middlewaru služby IIS zabránila zachovávání řetězce dotazu v pravidlech pro přepsání. Tato vada byla opravena, aby zachovala konzistenci s chováním modulu IIS UrlRewrite.

Diskuzi najdete v tématu problém [dotnet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972).

#### <a name="version-introduced"></a>Představená verze

ASP.NET Core 5,0 Preview 7

#### <a name="old-behavior"></a>Staré chování

Vezměte v úvahu následující pravidlo přepsání:

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

Předchozí pravidlo nepřipojí řetězec dotazu. Identifikátor URI, jako je `/about?id=1` přesměrování na `/contact` místo `/contact?id=1` . `appendQueryString`Výchozí hodnota atributu je `true` také.

#### <a name="new-behavior"></a>Nové chování

Řetězec dotazu se zachová. Identifikátor URI z příkladu ve [starém chování](#old-behavior) by byl `/contact?id=1` .

#### <a name="reason-for-change"></a>Důvod změny

Původní chování se neshodovalo s chováním modulu IIS UrlRewrite. Aby bylo možné podporovat přenos mezi middlewarem a modulem, je cílem zachovat konzistentní chování.

#### <a name="recommended-action"></a>Doporučená akce

Pokud je upřednostňováno chování při odebírání řetězce dotazu, nastavte `action` element na `appendQueryString="false"` .

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
