### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>Kódy chyb pro maxRequestLength nebo maxReceivedMessageSize se liší

|   |   |
|---|---|
|Podrobnosti|Zprávy ve WCF web služby hostované v Internetové informační služby (IIS) nebo vývojový Server ASP.NET, které překračují maxRequestLength (technologie ASP.NET) nebo maxReceivedMessageSize (ve službě WCF) mají různé chyby stavový kód codeThe HTTP se změnil z hodnoty 400 (Chybný požadavek ) 413 (požádat o Entity příliš velký) a zprávy, které překročí maxRequestLength nebo nastavení maxReceivedMessageSize throw <xref:System.ServiceModel.ProtocolException?displayProperty=name> výjimka. To zahrnuje případy, ve kterých je streamování režim přenosu.|
|Návrh|Tato změna usnadňuje ladění v případech, kde délka zpráva překračuje omezení povolenou technologie ASP.NET nebo WCF. Je třeba upravit kód, který provádí zpracování podle stavový kód HTTP 400.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|

