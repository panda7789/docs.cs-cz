### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>Trvalost SQL pracovního postupu přidává primární klíč clusterů a zakáže hodnoty null v některé sloupce

|   |   |
|---|---|
|Podrobnosti|Od verze 4.7 rozhraní .NET Framework, použijte tabulky pro SQL pracovního postupu Instance Store (SWIS) vytvořený skript SqlWorkflowInstanceStoreSchema.sql clusterovaný primární klíče. Z toho důvodu se nepodporují identity <code>null</code> hodnoty. Operaci SWIS není touto změnou ovlivněná. Aktualizace byly provedeny na podporu transakční replikace SQL serveru.|
|Návrh|Soubor SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql je nutné použít na existující instalace, aby bylo možné zaznamenat tuto změnu. Nové instalace databáze automaticky budou mít změny.|
|Rozsah|Edge|
|Version|4.7|
|Typ|modul runtime|

