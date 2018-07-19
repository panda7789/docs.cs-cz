### <a name="certificate-eku-oid-validation"></a>OID rozšířeného použití klíče ověření certifikátu

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6, <xref:System.Net.Security.SslStream> nebo <xref:System.Net.ServicePointManager> třídy provést ověření identifikátor (OID) objektu rozšířené použití klíče (EKU). Kolekce identifikátorů objektu (OID), které označují aplikace, které používají klíč je rozšíření rozšířené použití klíče (EKU). OID rozšířeného použití klíče ověření používá zpětná volání vzdálený certifikát a ujistěte se, že vzdálený certifikát mají správné identifikátory OID pro zamýšlený účel.|
|Návrh|Pokud tuto změnu nežádoucí, můžete zakázat certifikát OID rozšířeného použití klíče ověření tak, že přidáte následující přepnout na [ \<AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) v [ ` ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) z vaší konfigurační soubor aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Toto nastavení je dostupné pouze z důvodů zpětné kompatibility. Jeho použití v opačném případě se nedoporučuje.</blockquote> |
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

