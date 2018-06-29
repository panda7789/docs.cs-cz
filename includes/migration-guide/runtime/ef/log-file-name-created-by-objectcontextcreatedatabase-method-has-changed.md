### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>Došlo ke změně názvu souboru protokolu vytvářené metodou ObjectContext.CreateDatabase tak, aby odpovídaly specifikace systému SQL Server

|   |   |
|---|---|
|Podrobnosti|Když <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> metoda je volána buď přímo nebo pomocí Code First poskytovatel Sqlclienta a AttachDBFilename hodnotu v připojovacím řetězci, vytvoří soubor protokolu s názvem filename_log.ldf místo filename.ldf (kde název souboru je název soubor určený touto AttachDBFilename hodnota). Tato změna zlepšuje ladění poskytnutím souboru protokolu s názvem podle specifikace serveru SQL Server.|
|Návrh|Pokud název souboru protokolu je důležité pro aplikaci, je třeba aktualizovat aplikaci můžete očekávat formát názvu souboru standardní _log.ldf.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|

