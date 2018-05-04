### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Rozdělení výslovný souhlas se z různých 4.5 generování SQL vrátit k uložené jednodušší 4.0 generování SQL

|   |   |
|---|---|
|Podrobnosti|Dotazy, které vytvářejí Příkazy JOIN a obsahovat volání limitující operaci bez předchozího použití OrderBy nyní vytvořit jednodušší SQL. Po upgradu na rozhraní .NET Framework 4.5, byly tyto dotazy SQL složitější než předchozí verze.|
|Návrh|Tato funkce je ve výchozím nastavení vypnutá. Pokud rozhraní Entity Framework vygeneruje další příkazy spojení, které způsobí snížení výkonu, můžete povolit tuto funkci přidáním následující položku na <code>&lt;appSettings&gt;</code> části souboru aplikace (app.config) konfigurace:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Transparentní|
|Version|4.5.2|
|Typ|Modul runtime|

