### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Algoritmy výchozí SignedXML a SignedXMS změnit tak, aby SHA256

|   |   |
|---|---|
|Podrobnosti|4.7 rozhraní .NET Framework a starší SignedXML a SignedCMS výchozí SHA1 pro některé operace. Od verze rozhraní .NET Framework 4.7.1, je ve výchozím nastavení pro tyto operace povolené SHA256. Tuto změnu je nutné, protože již bylo zabezpečené, SHA1.|
|Návrh|Existují dva nové hodnoty kontextu přepínače na ovládací prvek, zda SHA1 (nezabezpečené) nebo SHA256 se používá ve výchozím nastavení:<ul><li>Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</li><li>Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms</li></ul>Pro aplikace, že cílové rozhraní .NET Framework 4.7.1 a novější verze, pokud použití SHA256 není žádoucí, můžete obnovit výchozí SHA1 přidáním následující konfigurace přepnout [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části souboru config aplikace soubor:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true&quot; /&gt;&#13;&#10;</code></pre>Pro aplikace, které cílí na rozhraní .NET Framework 4.7 a starší verze, se můžete rozhodnout do tuto změnu přidáním následující konfigurace přepínač tak, aby [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části souboru config aplikace:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType></li></ul>|

