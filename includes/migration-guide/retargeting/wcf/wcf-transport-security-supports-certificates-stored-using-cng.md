---
ms.openlocfilehash: 8c1ca89af289dbcc6c68d5ace3e8a9f32672ec0d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859286"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>Zabezpečení přenosu WCF podporuje certifikáty na Uložit pomocí CNG

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací využívajících rozhraní .NET Framework 4.6.2, podporuje zabezpečení přenosu WCF certifikáty uložené, pomocí knihovny šifrování Windows (CNG). Tato podpora je omezena na certifikáty s veřejným klíčem, který má v délka exponentu více než 32 bitů. Pokud aplikace cílí na .NET Framework 4.6.2, tato funkce je ve výchozím. V dřívějších verzích rozhraní .NET Framework, pokus o použití X509 certifikáty CSG vyvolá výjimku, zprostředkovatel úložiště klíčů.|
|Doporučení|Aplikace, které cílové rozhraní .NET Framework 4.6.1 a starší ale jsou spuštěny v rozhraní .NET Framework 4.6.2 můžete povolit podporu certifikátů CNG tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config nebo web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>To je možné provést prostřednictvím kódu programu následujícím kódem:<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Všimněte si, že se z důvodu této změny, už žádné výjimce kód, který je závislý na pokus o inicializaci zabezpečenou komunikaci s certifikátem CNG selhání zpracování spustí.|
|Scope|Vedlejší|
|Version|4.6.2|
|type|Změna cílení|

