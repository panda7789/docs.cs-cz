### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce podporuje SHA-256 na 4.0 cílové aplikace

|   |   |
|---|---|
|Podrobnosti|Aplikace ClickOnce pomocí certifikát podepsaný pomocí algoritmu SHA-256 dříve, musel by nacházet, i v případě, že cílem aplikace 4.0 rozhraní .NET Framework 4.5 nebo novější. Nyní cílové rozhraní .NET Framework 4.0 ClickOnce aplikace můžete spustit v rozhraní .NET Framework 4.0, i když podepsané pomocí algoritmu SHA-256.|
|Návrh|Tato změna odebere této závislosti a umožňuje certifikáty SHA-256 k podepisování aplikací ClickOnce, které cílí na rozhraní .NET Framework 4 a starší verze.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna orientace|

