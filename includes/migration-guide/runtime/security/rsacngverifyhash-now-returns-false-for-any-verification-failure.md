### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash nyní vrací hodnotu False pro jakékoli neúspěchy ověření

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6.2, vrátí tato metoda <strong>False</strong> Pokud samotný podpis má chybný formát. Nyní vrací hodnotu false pro všechny chyby ověření. V rozhraní .NET Framework 4.6 a 4.6.1, vyvolá metoda výjimku <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> Pokud samotný podpis má chybný formát.|
|Doporučení|Jakýkoli kód, jejichž spuštění závisí na zpracování <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> by se měl spustit místo toho, pokud ověření selže a metoda vrátí <strong>False</strong>.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

