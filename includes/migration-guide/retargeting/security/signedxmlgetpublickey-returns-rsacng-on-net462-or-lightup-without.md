### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey vrátí RSACng na net462 (nebo lightup) bez Změna orientace změn

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6.2, na konkrétní typ objektu vrácený <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> metodu změnit (bez datového toku zvuku nabízí) z implementace CryptoServiceProvider Cng implementaci. Důvodem je, že implementace změnila pomocí <code>certificate.PublicKey.Key</code> pomocí interní <code>certificate.GetAnyPublicKey</code> který předává <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.|
|Návrh|Počínaje aplikací běžících na rozhraní .NET Framework 4.7.1, můžete použít CryptoServiceProvider implementace používá ve výchozím nastavení v rozhraní .NET Framework 4.6.1 a starší verze přidáním následující konfigurace přepnout [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)části souboru config aplikace:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|

