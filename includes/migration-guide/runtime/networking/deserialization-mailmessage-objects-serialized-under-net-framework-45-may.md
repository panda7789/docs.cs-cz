### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>Deserializace MailMessage objekty serializované v rozhraní .NET Framework 4.5 může selhat.

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objekty může obsahovat jiné znaky než ASCII. V rozhraní .NET Framework 4 jsou podporovány pouze znaky ASCII. <xref:System.Web.Mail.MailMessage> objekty, které obsahují ne ASCII znaky a, které jsou serializovány v rozhraní .NET Framework 4.5 nebo novější, nemohou být deserializovány v rozhraní .NET Framework 4.|
|Návrh|Ujistěte se, že váš kód obsahuje zpracování výjimek při deserializaci <xref:System.Web.Mail.MailMessage> objektu.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|

