### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet.FindClaims považovat všechny claimTypes

|   |   |
|---|---|
|Podrobnosti|V aplikacích, které cílí na rozhraní .NET Framework 4.6.1, pokud sada deklarací identity je inicializován ze certifikát, který obsahuje několik záznamů DNS v jeho poli SAN X509 <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda se pokusí o porovnání argument typ claimType s všechny záznamy DNS. Pro aplikace, které cílí na předchozích verzích rozhraní .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda se pokusí o porovnání argument typ claimType pouze s poslední položky DNS.|
|Návrh|Tato změna ovlivní pouze aplikace cílený na rozhraní .NET Framework 4.6.1. Tato změna mohou být zakázány (nebo -li povolena které se budou zaměřovat pre-4.6.1) s [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) kompatibility přepínače.|
|Rozsah|Vedlejší|
|Version|4.6.1|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

