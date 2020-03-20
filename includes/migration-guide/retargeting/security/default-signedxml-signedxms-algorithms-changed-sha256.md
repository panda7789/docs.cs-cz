---
ms.openlocfilehash: db076d6799e4de5b8610cf9c1aac79b5386a7229
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859049"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Výchozí algoritmy SignedXML a SignedXMS byly změněny na SHA256.

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7 a starší signedxml a signedcms výchozí SHA1 pro některé operace. Počínaje rozhraním .NET Framework 4.7.1 je sha256 pro tyto operace ve výchozím nastavení povolen. Tato změna je nezbytná, protože SHA1 již není považován za zabezpečený.|
|Návrh|Existují dvě nové hodnoty přepínacího kontextu, které řídí, zda se sha1 (nezabezpečené) nebo SHA256 používá ve výchozím nastavení:<ul><li>Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</li><li>Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms</li></ul>Pro aplikace, které cílí na rozhraní .NET Framework 4.7.1 a novější verze, pokud je použití SHA256 nežádoucí, můžete obnovit výchozí sha1 přidáním následujícího konfiguračního přepínače do sekce [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true&quot; /&gt;&#13;&#10;</code></pre>U aplikací, které cílí na rozhraní .NET Framework 4.7 a starší verze, se můžete do této změny přihlásit přidáním následujícího konfiguračního přepínače do části [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType></li></ul>|
