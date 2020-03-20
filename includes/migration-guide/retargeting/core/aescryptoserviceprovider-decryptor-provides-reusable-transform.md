---
ms.openlocfilehash: c008809606372c84b05a2facd1cac1293382aed4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859361"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Dešifrátor AesCryptoServiceProvider poskytuje opakovaně použitelnou transformaci

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.2, <xref:System.Security.Cryptography.AesCryptoServiceProvider> dešifrovací program poskytuje opakovaně použitelnou transformaci. Po volání <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name>, transformace je reinitialized a lze znovu použít. Pro aplikace, které cílí na starší verze rozhraní .NET Framework, <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> pokus u <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> opětovného <xref:System.Security.Cryptography.CryptographicException> použití decryptor voláním po volání vyvolá nebo vytváří poškozená data.|
|Návrh|Dopad této změny by měla být minimální, protože se jedná o očekávané chování. Aplikace, které závisí na předchozím chování, se z něj mohou <code>&lt;runtime&gt;</code> odhlásit přidáním následujícího nastavení konfigurace do části konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Kromě toho se aplikace, které cílí na předchozí verzi rozhraní .NET Framework, ale jsou spuštěny v rámci verze rozhraní .NET Framework <code>&lt;runtime&gt;</code> začínající rozhraním .NET Framework 4.6.2, mohou přihlásit přidáním následujícího nastavení konfigurace do části konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|
