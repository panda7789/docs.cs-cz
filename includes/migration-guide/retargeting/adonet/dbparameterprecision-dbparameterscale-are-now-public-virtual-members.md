### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>DbParameter.Precision a DbParameter.Scale jsou teď virtuální veřejné členy

|   |   |
|---|---|
|Podrobnosti|<xref:System.Data.Common.DbParameter.Precision> a <xref:System.Data.Common.DbParameter.Scale> jsou implementovány jako virtuální veřejné vlastnosti. Nahrazují odpovídající implementace explicitního rozhraní <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> a <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.|
|Návrh|Při opětovné sestavování databáze poskytovatele ADO.NET, bude vyžadovat tyto rozdíly – klíčové slovo 'override' má použít u vlastnosti hodnot Precision a Scale. To je jenom nutné, když znovu sestavení součástí; existující binární soubory budou nadále fungovat.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|

