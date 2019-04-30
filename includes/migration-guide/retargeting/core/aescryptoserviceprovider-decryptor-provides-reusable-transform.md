---
ms.openlocfilehash: c008809606372c84b05a2facd1cac1293382aed4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639466"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Opakovaně použitelné transformace poskytuje AesCryptoServiceProvider modul pro dešifrování.

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací určených pro rozhraní .NET Framework 4.6.2, <xref:System.Security.Cryptography.AesCryptoServiceProvider> modul pro dešifrování. nabízí opakovaně použitelné transformace. Po volání <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name>, transformací, která se budou znovu inicializována a je možné využít znovu. Pro aplikace, které jsou cíleny na starší verze rozhraní .NET Framework, pokus o opakované použití modul pro dešifrování voláním <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> po volání <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> vyvolá <xref:System.Security.Cryptography.CryptographicException> nebo je výsledný poškozená data.|
|Doporučení|Dopad této změny by mělo minimální, protože se jedná o očekávané chování. Aplikace, které závisí na předchozím chování můžete vyjádřit výslovný nesouhlas pomocí přidáním následujícího nastavení konfigurace <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Kromě toho aplikace, které cílí předchozí verzi rozhraní .NET Framework, ale jsou spuštěny na verzi rozhraní .NET Framework počínaje .NET Framework 4.6.2 můžete přejít k to tak, že přidáte následující konfigurační nastavení <code>&lt;runtime&gt;</code> část konfigurační soubor aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|
