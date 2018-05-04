### <a name="certificate-eku-oid-validation"></a>Ověření OID rozšířeného použití klíče certifikátu

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6 <xref:System.Net.Security.SslStream> nebo <xref:System.Net.ServicePointManager> třídy provést ověření identifikátor (OID) objekt rozšířené použití klíče (EKU). Kolekce identifikátorů objektů (OID), které označují aplikace, které používají klíče je rozšíření rozšířené použití klíče (EKU). OID rozšířeného použití klíče ověření používá zpětná volání vzdálený certifikát k zajištění, že vzdálený certifikát má správný identifikátorů oid pro zamýšlený účel.|
|Návrh|Pokud tato změna není žádoucí, můžete zakázat certifikát OID rozšířeného použití klíče ověření přidáním následující přepnout [ \<AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) v [ ` ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) z vaší soubor konfigurace aplikací:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Toto nastavení je dostupné pouze z důvodů zpětné kompatibility. V opačném případě se nedoporučuje používat.</blockquote> |
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

