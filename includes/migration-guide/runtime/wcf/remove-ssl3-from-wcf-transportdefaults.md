### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Odebrání Ssl3 WCF TransportDefaults

|   |   |
|---|---|
|Podrobnosti|Při použití NetTcp s zabezpečení přenosu a typ přihlašovacích údajů certifikátu, je výchozím protokolem pro vyjednávání zabezpečené připojení už protokol SSL 3. Ve většině případů je třeba mít žádný vliv na stávající aplikace jako TLS 1.0 vždy byl zahrnut v seznamu protokolů pro NetTcp. Všichni existující klienti byste měli mít připojení pomocí na minimálně TLS1.0.|
|Návrh|Pokud Ssl3 je potřeba, použijte jednu z následujících mechanismů konfigurace Ssl3 přidat do seznamu vyjednané protokolů.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; části &lt;customBinding&gt;] ~ / docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|

