---
ms.openlocfilehash: 846a6bcd3c668e6ad505f745bcb830c3b9dce437
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859361"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Opakovaně použitelné transformace poskytuje AesCryptoServiceProvider modul pro dešifrování.

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací určených pro rozhraní .NET Framework 4.6.2, <xref:System.Security.Cryptography.AesCryptoServiceProvider> modul pro dešifrování. nabízí opakovaně použitelné transformace. Po volání <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name>, transformací, která se budou znovu inicializována a je možné využít znovu. Pro aplikace, které jsou cíleny na starší verze rozhraní .NET Framework, pokus o opakované použití modul pro dešifrování voláním <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> po volání <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> vyvolá <xref:System.Security.Cryptography.CryptographicException> nebo je výsledný poškozená data.|
|Doporučení|Dopad této změny by mělo minimální, protože se jedná o očekávané chování. Aplikace, které závisí na předchozím chování můžete vyjádřit výslovný nesouhlas pomocí přidáním následujícího nastavení konfigurace <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Kromě toho aplikace, které cílí předchozí verzi rozhraní .NET Framework, ale jsou spuštěny na verzi rozhraní .NET Framework počínaje .NET Framework 4.6.2 můžete přejít k to tak, že přidáte následující konfigurační nastavení <code>&lt;runtime&gt;</code> část konfigurační soubor aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.6.2|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|

