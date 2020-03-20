---
ms.openlocfilehash: b57e0acb03a99f33460a7b6c880280b37e01a17b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859286"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>WCF zabezpečení přenosu podporuje certifikáty uložené pomocí CNG

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.2, podporuje zabezpečení přenosu WCF certifikáty uložené pomocí knihovny Kryptografie systému Windows (CNG). Tato podpora je omezena na certifikáty s veřejným klíčem, který má exponent ne více než 32 bitů na délku. Pokud aplikace cílí na rozhraní .NET Framework 4.6.2, je tato funkce ve výchozím nastavení zapnutá. V dřívějších verzích rozhraní .NET Framework pokus o použití certifikátů X509 s poskytovatelem úložiště klíčů CSG vyvolá výjimku.|
|Návrh|Aplikace, které cílí na rozhraní .NET Framework 4.6.1 a starší, ale jsou spuštěny v rozhraní .NET <code>&lt;runtime&gt;</code> Framework 4.6.2, mohou povolit podporu certifikátů CNG přidáním následujícího řádku do části souboru app.config nebo web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>To lze také provést programově s následujícím kódem:<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Všimněte si, že z důvodu této změny žádné výjimky zpracování kódu, který závisí na pokusu o zahájení zabezpečené komunikace s certifikátem CNG nezdaří již nebude spuštěna.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Změna cílení|
