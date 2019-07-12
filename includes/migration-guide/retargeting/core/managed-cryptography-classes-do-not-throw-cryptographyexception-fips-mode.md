---
ms.openlocfilehash: 2b768047a8b08501a8de4666d240072318427f28
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803493"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a>Spravované třídy šifrování nevyvolají výjimku CryptographyException v režimu FIPS

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.2 a dřívějších verzích spravované třídy zprostředkovatele kryptografických služeb <xref:System.Security.Cryptography.SHA256Managed> vyvolat <xref:System.Security.Cryptography.CryptographicException> při kryptografické knihovny systému jsou nakonfigurované v režimu FIPS. Vyvolání těchto výjimek vzhledem k tomu, že spravovaná verze neprošel certifikaci 140-2, stejně jako blokování kryptografických algoritmů, které se nezohledňovaly schválení na základě FIPS pravidel standardu FIPS (Federal Information Processing Standards).  Protože několik vývojáři mají své vývojové počítače v režimu FIPS, vyvolání těchto výjimek často jenom na provozní systémy. Aplikací určených pro rozhraní .NET Framework 4,8 a novějších verzích automaticky přepnout na novější, volný zásady, tak, aby <xref:System.Security.Cryptography.CryptographicException> je již vyvolána ve výchozím nastavení v těchto případech. Místo toho spravované třídy šifrování přesměrování kryptografických operací na systémová knihovna kryptografie. Tato změna zásady účinně odstraní potenciálně matoucí rozdíl mezi produkční prostředí a prostředí pro vývojáře a zpřístupňuje nativní součásti a spravované komponenty pracovat v rámci stejné Kryptografické zásady.|
|Doporučení|Pokud toto chování nežádoucí, můžete odhlásit a obnovení předchozího chování tak, která <xref:System.Security.Cryptography.CryptographicException> je vyvolána v režimu FIPS přidáním následujícího kódu [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) nastavení konfigurace [ <runtime> ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.UseLegacyFipsThrow=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pokud vaše aplikace cílí na .NET Framework 4.7.2 nebo dříve, můžete také přejít k této změně přidáním následujícího kódu [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) nastavení konfigurace [ <runtime> ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddíl konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.UseLegacyFipsThrow=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.8|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType></li></ul>|

