### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>Sdílení stavu relace s Asp.Net StateServer vyžaduje všechny servery ve webové farmě, aby používal stejnou verzi rozhraní .NET Framework

|   |   |
|---|---|
|Podrobnosti|Při povolování <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> stavu relace, všechny servery v dané webové farmě musí používat stejnou verzi rozhraní .NET Framework v pořadí pro stav tak, aby správně sdílené.|
|Návrh|Ujistěte se, že upgrade verze rozhraní .NET Framework na webových serverech, které sdílejí stavu ve stejnou dobu.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|

