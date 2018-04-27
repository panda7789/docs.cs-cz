### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime.AppDomainAppPath vyvolá výjimky NullReferenceException.

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 modul runtime vyvolá <code>T:System.NullReferenceException</code> při načítání <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> hodnotu, která zahrnuje znaky null. V rozhraní .NET Framework 4.6.1 a dřívějších verzí, modul runtime vyvolá <code>T:System.ArgumentNullException</code>.|
|Návrh|Můžete provést jeden z těchto kroků reagovat na tuto změnu:<ul><li>Zpracování <code>T:System.NullReferenceException</code> Pokud je aplikace spuštěna v rozhraní .NET Framework 4.6.2.</li><li>Upgrade na 4.7 Framework .NET, která obnoví předchozí chování a způsobí výjimku, <code>T:System.ArgumentNullException</code>.</li></ul>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

