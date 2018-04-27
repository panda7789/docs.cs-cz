### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>DbParameter.Precision a DbParameter.Scale jsou teď virtuální veřejné členy

|   |   |
|---|---|
|Podrobnosti|<xref:System.Data.Common.DbParameter.Precision> a <xref:System.Data.Common.DbParameter.Scale> jsou implementované jako veřejné virtuální vlastnosti. Nahrazují odpovídající implementace explicitního rozhraní, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> a <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.|
|Návrh|Při sestavování znovu poskytovatele ADO.NET databáze, bude vyžadovat tyto rozdíly – klíčové slovo 'override' má být použita pro vlastnosti přesnost a měřítko. Toto je vyžadováno pouze při opětovné vytváření komponenty; existující binární soubory budou nadále fungovat.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|

