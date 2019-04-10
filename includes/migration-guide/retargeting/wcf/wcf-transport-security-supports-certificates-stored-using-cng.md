---
ms.openlocfilehash: b57e0acb03a99f33460a7b6c880280b37e01a17b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234896"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>Zabezpečení přenosu WCF podporuje certifikáty na Uložit pomocí CNG

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací využívajících rozhraní .NET Framework 4.6.2, podporuje zabezpečení přenosu WCF certifikáty uložené, pomocí knihovny šifrování Windows (CNG). Tato podpora je omezena na certifikáty s veřejným klíčem, který má v délka exponentu více než 32 bitů. Pokud aplikace cílí na .NET Framework 4.6.2, tato funkce je ve výchozím. V dřívějších verzích rozhraní .NET Framework, pokus o použití X509 certifikáty CSG vyvolá výjimku, zprostředkovatel úložiště klíčů.|
|Doporučení|Aplikace, které cílové rozhraní .NET Framework 4.6.1 a starší ale jsou spuštěny v rozhraní .NET Framework 4.6.2 můžete povolit podporu certifikátů CNG tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config nebo web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>To je možné provést prostřednictvím kódu programu následujícím kódem:<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Všimněte si, že se z důvodu této změny, už žádné výjimce kód, který je závislý na pokus o inicializaci zabezpečenou komunikaci s certifikátem CNG selhání zpracování spustí.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Type|Změna cílení|
