### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash nyní vrátí hodnotu False, pro žádné ověření se nezdařilo

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6.2, vrátí tato metoda <strong>False</strong> Pokud podpis samotné chybně formátována. Nyní vrací hodnotu false pro žádné ověření se nezdařilo. V rozhraní .NET Framework 4.6 a 4.6.1, vyvolá metoda <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> Pokud podpis samotné chybně formátována.|
|Návrh|Kód, jejichž provedení závisí na zpracování <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> by měl místo toho provést, pokud ověření selže a metoda vrátí <strong>False</strong>.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

