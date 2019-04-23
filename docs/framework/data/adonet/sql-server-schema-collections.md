---
title: Kolekce schémat SQL Serveru
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: 79bf9f1253b64863d3eabddff8c33b6ffab70f41
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224554"
---
# <a name="sql-server-schema-collections"></a>Kolekce schémat SQL Serveru
Poskytovatel dat rozhraní Microsoft .NET Framework pro SQL Server podporuje další schéma kolekce kromě společné kolekce schémat. Kolekce schémat mírně lišit podle verze SQL serveru, který používáte. Pokud chcete určit seznam kolekcí nepodporuje schéma, zavolejte **GetSchema** metody bez argumentů nebo názvem kolekce schématu "MetaDataCollections". Vrátí <xref:System.Data.DataTable> seznam kolekcí nepodporuje schéma, počet omezení, které každá podporují a počet identifikátor částí, které používají.  
  
## <a name="databases"></a>Databáze  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|Název databáze database_name|String|Název databáze.|  
|DBID|Int16|ID databáze.|  
|create_date|DateTime|Datum vytvoření databáze.|  
  
## <a name="foreign-keys"></a>Cizí klíče  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|String|Katalog omezení patří.|  
|CONSTRAINT_SCHEMA|String|Schéma, které obsahuje omezení.|  
|CONSTRAINT_NAME|String|Jméno.|  
|TABLE_CATALOG|String|Omezení název tabulky je součástí.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku.|  
|TABLE_NAME|String|Název tabulky|  
|CONSTRAINT_TYPE|String|Typ omezení. Je povolen pouze "cizí klíč".|  
|IS_DEFERRABLE|String|Určuje, zda je omezení nebyla. Vrátí číslo|  
|INITIALLY_DEFERRED|String|Určuje, zda je zpočátku nebyla omezení. Vrátí číslo|  
  
## <a name="indexes"></a>Indexy  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, který patří indexu.|  
|constraint_schema|String|Schéma, které obsahuje index.|  
|constraint_name|String|Název indexu.|  
|TABLE_CATALOG|String|Název tabulky indexu je přidružený.|  
|table_schema|String|Schéma, které obsahuje tabulku indexu je přidružený.|  
|TABLE_NAME|String|Název tabulky.|  
|index_name|String|Název indexu.|  
  
### <a name="indexes-sql-server-2008"></a>Indexes (SQL Server 2008)  
 Od verze rozhraní .NET Framework verze 3.5 SP1 a SQL Server 2008, tyto sloupce se přidaly do kolekce schémat indexů pro podporu nových prostorových typů filestream a zhuštěné sloupce. Tyto sloupce nejsou podporovány v dřívějších verzích rozhraní .NET Framework a systému SQL Server.  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|type_desc|String|Typ indexu bude jeden z následujících akcí:<br /><br /> -HEAP<br />– V CLUSTERU<br />-NECLUSTEROVANÝ<br />-   XML<br />– PROSTOROVÝ|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, který patří indexu.|  
|constraint_schema|String|Schéma, které obsahuje index.|  
|constraint_name|String|Název indexu.|  
|TABLE_CATALOG|String|Název tabulky indexu je přidružený.|  
|table_schema|String|Schéma, které obsahuje tabulku indexu je přidružený.|  
|TABLE_NAME|String|Název tabulky.|  
|COLUMN_NAME|String|Název sloupce indexu je přidružený.|  
|ordinal_position|Int32|Pořadí sloupců.|  
|KeyType|Byte|Typ objektu.|  
|index_name|String|Název indexu.|  
  
## <a name="procedures"></a>Procedury  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Konkrétní název katalogu.|  
|SPECIFIC_SCHEMA|String|Konkrétní název schématu.|  
|SPECIFIC_NAME|String|Konkrétní název katalogu.|  
|ROUTINE_CATALOG|String|Katalog uložené procedury patří.|  
|ROUTINE_SCHEMA|String|Schéma, které obsahuje uložené procedury.|  
|ROUTINE_NAME|String|Název uložené procedury.|  
|ROUTINE_TYPE|String|Postup pro uložené procedury a funkce vrátí pro funkce.|  
|VYTVOŘENÍ|DateTime|Čas vytvoření procesu.|  
|LAST_ALTERED|DateTime|Čas poslední postup byla změněna.|  
  
## <a name="procedure-parameters"></a>Parametry procedur  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Název procedury, pro kterou je toto parametr katalogu.|  
|SPECIFIC_SCHEMA|String|Schéma, který obsahuje postup, pro které tento parametr je součástí.|  
|SPECIFIC_NAME|String|Název procedury, pro které tento parametr je součástí.|  
|ORDINAL_POSITION|Int32|Pořadové číslo pozice parametru začínající hodnotou 1. Pro vrácené hodnoty procedury Toto je 0.|  
|PARAMETER_MODE|String|Vrátí v případě vstupní parametr, na co si výstupní parametr a INOUT Pokud vstupní/výstupní parametr.|  
|IS_RESULT|String|Vrátí hodnotu Ano, pokud určuje výsledek postup, který je funkce. V opačném případě vrátí číslo.|  
|AS_LOCATOR|String|Vrátí hodnotu Ano, pokud deklarovaný jako Lokátor. V opačném případě vrátí číslo.|  
|PARAMETER_NAME|String|Název parametru Hodnota NULL, pokud to odpovídá na návratový typ funkce.|  
|DATA_TYPE|String|Poskytnuté systémem datového typu.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maximální délka ve znacích pro typy binární nebo znaková data. V opačném případě vrátí hodnotu NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maximální délka v bajtech binárního nebo znak datových typů. V opačném případě vrátí hodnotu NULL.|  
|COLLATION_CATALOG|String|Název katalogu kolaci parametru. Pokud není jeden z těchto typů znaků, vrátí hodnotu NULL.|  
|COLLATION_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|COLLATION_NAME|String|Název kolace parametru. Pokud není jeden z těchto typů znaků, vrátí hodnotu NULL.|  
|CHARACTER_SET_CATALOG|String|Název katalogu znaku nastavení parametru. Pokud není jeden z těchto typů znaků, vrátí hodnotu NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Název znakové sady parametru. Pokud není jeden z těchto typů znaků, vrátí hodnotu NULL.|  
|NUMERIC_PRECISION|Byte|Přesnost přibližné číselná data, přesné číselná data, data celé číslo nebo peněžní data. V opačném případě vrátí hodnotu NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Precision základ číselné soustavy přibližné číselná data, přesné číselná data, celočíselných dat nebo peněžní data. V opačném případě vrátí hodnotu NULL.|  
|NUMERIC_SCALE|Int32|Měřítko přibližné číselná data, přesné číselná data, data celé číslo nebo peněžní data. V opačném případě vrátí hodnotu NULL.|  
|DATETIME_PRECISION|Int16|Přesnost v zlomků sekund, pokud je typ parametru datetime nebo smalldatetime. V opačném případě vrátí hodnotu NULL.|  
|INTERVAL_TYPE|String|HODNOTA NULL. Vyhrazeno pro budoucí použití nástrojem SQL Server.|  
|INTERVAL_PRECISION|Int16|HODNOTA NULL. Vyhrazeno pro budoucí použití nástrojem SQL Server.|  
  
## <a name="tables"></a>Tabulky  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku.|  
|TABLE_NAME|String|Název tabulky.|  
|TABLE_TYPE|String|Typ tabulky. Může být zobrazení nebo základní tabulku.|  
  
## <a name="columns"></a>Sloupce  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku.|  
|TABLE_NAME|String|Název tabulky.|  
|COLUMN_NAME|String|Název sloupce.|  
|ORDINAL_POSITION|Int32|Identifikační číslo sloupce.|  
|COLUMN_DEFAULT|String|Výchozí hodnota sloupce|  
|IS_NULLABLE|String|Možnost použití hodnoty NULL sloupce. Pokud tento sloupec povoluje hodnotu NULL, vrátí se v tomto sloupci Ano. V opačném případě ne je vrácena.|  
|DATA_TYPE|String|Poskytnuté systémem datového typu.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7|Maximální délka ve znacích pro binární data, znaková data nebo textových a obrázkových data. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|Maximální délka v bajtech pro binární data, znaková data nebo textových a obrázkových data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION|Typ bajt bez znaménka|Přesnost přibližné číselná data, přesné číselná data, data celé číslo nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Precision základ číselné soustavy přibližné číselná data, přesné číselná data, celočíselných dat nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_SCALE|Int32|Měřítko přibližné číselná data, přesné číselná data, data celé číslo nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|DATETIME_PRECISION|Int16|Podtyp kód SQL 92 interval datové typy a data a času. Pro ostatní typy dat je vrácena hodnota NULL.|  
|CHARACTER_SET_CATALOG|String|Vrátí hlavní, označující databáze, ve kterém se nachází, znakové sady, jestli je sloupec znaková data nebo textová data typu. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Vrátí jedinečný název pro znak nastavte, pokud je tento sloupec znaková data nebo textová data typu. V opačném případě je vrácena hodnota NULL.|  
|COLLATION_CATALOG|String|Vrátí hlavní, určující databáze, ve kterém je definována kolaci, pokud je ve sloupci znaková data nebo textová data typu. V tomto sloupci, jinak má hodnotu NULL.|  
  
### <a name="columns-sql-server-2008"></a>Columns (SQL Server 2008)  
 Od verze rozhraní .NET Framework verze 3.5 SP1 a SQL Server 2008, tyto sloupce se přidaly do kolekce schémat sloupců pro podporu nových prostorových typů filestream a zhuštěné sloupce. Tyto sloupce nejsou podporovány v dřívějších verzích rozhraní .NET Framework a systému SQL Server.  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|String|Ano, pokud se tento sloupec měl atributem FILESTREAM.<br /><br /> Ne, pokud sloupec neobsahuje atribut FILESTREAM.|  
|IS_SPARSE|String|Ano, pokud je ve sloupci sadu zhuštěných sloupců.<br /><br /> Ne, pokud sloupec není sadu zhuštěných sloupců.|  
|IS_COLUMN_SET|String|Ano, pokud sloupec je sloupec sady sloupců.<br /><br /> Ne, pokud sloupec není sloupec sady sloupců.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 Od verze rozhraní .NET Framework verze 3.5 SP1 a SQL Server 2008, přidala se AllColumns kolekci schémat pro podporu zhuštěné sloupce. AllColumns není podporované v dřívějších verzích rozhraní .NET Framework a systému SQL Server.  
  
 AllColumns má stejná omezení a výsledný schéma objektu DataTable jako kolekce schémat sloupců. Jediným rozdílem je, že AllColumns obsahuje sloupec sady sloupců, které nejsou zahrnuty v kolekci schémat sloupců. Následující tabulka popisuje tyto sloupce.  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku.|  
|TABLE_NAME|String|Název tabulky.|  
|COLUMN_NAME|String|Název sloupce.|  
|ORDINAL_POSITION|Int32|Identifikační číslo sloupce.|  
|COLUMN_DEFAULT|String|Výchozí hodnota sloupce|  
|IS_NULLABLE|String|Možnost použití hodnoty NULL sloupce. Pokud tento sloupec povoluje hodnotu NULL, vrátí se v tomto sloupci Ano. V opačném případě ne je vrácena.|  
|DATA_TYPE|String|Poskytnuté systémem datového typu.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maximální délka ve znacích pro binární data, znaková data nebo textových a obrázkových data. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maximální délka v bajtech pro binární data, znaková data nebo textových a obrázkových data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION|Typ bajt bez znaménka|Přesnost přibližné číselná data, přesné číselná data, data celé číslo nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Precision základ číselné soustavy přibližné číselná data, přesné číselná data, celočíselných dat nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_SCALE|Int32|Měřítko přibližné číselná data, přesné číselná data, data celé číslo nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|DATETIME_PRECISION|Int16|Podtyp kód SQL 92 interval datové typy a data a času. Pro ostatní typy dat je vrácena hodnota NULL.|  
|CHARACTER_SET_CATALOG|String|Vrátí hlavní, označující databáze, ve kterém se nachází, znakové sady, jestli je sloupec znaková data nebo textová data typu. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Vrátí jedinečný název pro znak nastavte, pokud je tento sloupec znaková data nebo textová data typu. V opačném případě je vrácena hodnota NULL.|  
|COLLATION_CATALOG|String|Vrátí hlavní, určující databáze, ve kterém je definována kolaci, pokud je ve sloupci znaková data nebo textová data typu. V tomto sloupci, jinak má hodnotu NULL.|  
|IS_FILESTREAM|String|Ano, pokud se tento sloupec měl atributem FILESTREAM.<br /><br /> Ne, pokud sloupec neobsahuje atribut FILESTREAM.|  
|IS_SPARSE|String|Ano, pokud je ve sloupci sadu zhuštěných sloupců.<br /><br /> Ne, pokud sloupec není sadu zhuštěných sloupců.|  
|IS_COLUMN_SET|String|Ano, pokud sloupec je sloupec sady sloupců.<br /><br /> Ne, pokud sloupec není sloupec sady sloupců.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 Od verze rozhraní .NET Framework verze 3.5 SP1 a SQL Server 2008, přidala se ColumnSetColumns kolekci schémat pro podporu zhuštěné sloupce. ColumnSetColumns není podporované v dřívějších verzích rozhraní .NET Framework a systému SQL Server. Kolekce schémat ColumnSetColumns vrací schéma pro všechny sloupce v sadě sloupců. Následující tabulka popisuje tyto sloupce.  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku.|  
|TABLE_NAME|String|Název tabulky.|  
|COLUMN_NAME|String|Název sloupce.|  
|ORDINAL_POSITION|Int32|Identifikační číslo sloupce.|  
|COLUMN_DEFAULT|String|Výchozí hodnota sloupce|  
|IS_NULLABLE|String|Možnost použití hodnoty NULL sloupce. Pokud tento sloupec povoluje hodnotu NULL, vrátí se v tomto sloupci Ano. V opačném případě ne je vrácena.|  
|DATA_TYPE|String|Poskytnuté systémem datového typu.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maximální délka ve znacích pro binární data, znaková data nebo textových a obrázkových data. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maximální délka v bajtech pro binární data, znaková data nebo textových a obrázkových data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION|Typ bajt bez znaménka|Přesnost přibližné číselná data, přesné číselná data, data celé číslo nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Precision základ číselné soustavy přibližné číselná data, přesné číselná data, celočíselných dat nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_SCALE|Int32|Měřítko přibližné číselná data, přesné číselná data, data celé číslo nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|DATETIME_PRECISION|Int16|Podtyp kód SQL 92 interval datové typy a data a času. Pro ostatní typy dat je vrácena hodnota NULL.|  
|CHARACTER_SET_CATALOG|String|Vrátí hlavní, označující databáze, ve kterém se nachází, znakové sady, jestli je sloupec znaková data nebo textová data typu. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Vrátí jedinečný název pro znak nastavte, pokud je tento sloupec znaková data nebo textová data typu. V opačném případě je vrácena hodnota NULL.|  
|COLLATION_CATALOG|String|Vrátí hlavní, určující databáze, ve kterém je definována kolaci, pokud je ve sloupci znaková data nebo textová data typu. V tomto sloupci, jinak má hodnotu NULL.|  
|IS_FILESTREAM|String|Ano, pokud se tento sloupec měl atributem FILESTREAM.<br /><br /> Ne, pokud sloupec neobsahuje atribut FILESTREAM.|  
|IS_SPARSE|String|Ano, pokud je ve sloupci sadu zhuštěných sloupců.<br /><br /> Ne, pokud sloupec není sadu zhuštěných sloupců.|  
|IS_COLUMN_SET|String|Ano, pokud sloupec je sloupec sady sloupců.<br /><br /> Ne, pokud sloupec není sloupec sady sloupců.|  
  
## <a name="users"></a>Uživatelé  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|uid|Int16|ID uživatele, v této databázi jedinečné. 1 je vlastníkem databáze.|  
|uživatelské_jméno|String|Uživatelské jméno nebo název skupiny, v této databázi jedinečné.|  
|CREATEDATE formát|DateTime|Datum, kdy byl přidán účet.|  
|updatedate|DateTime|Datum, kdy byl naposled změněn účet.|  
  
## <a name="views"></a>Zobrazení  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog zobrazení.|  
|TABLE_SCHEMA|String|Schéma, která obsahuje zobrazení.|  
|TABLE_NAME|String|Název zobrazení.|  
|CHECK_OPTION|String|Typ s možností vrácení. Pokud původní zobrazení byl vytvořen pomocí WITH CHECK OPTION, je CASCADE. Jinak se vrátí NONE.|  
|IS_UPDATABLE|String|Určuje, zda je zobrazení aktualizovat. Vždy vrátí číslo.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|String|Katalog zobrazení.|  
|VIEW_SCHEMA|String|Schéma, která obsahuje zobrazení.|  
|VIEW_NAME|String|Název zobrazení.|  
|TABLE_CATALOG|String|Katalog, který je přidružený k tomuto zobrazení tabulky.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku, která je přidružená k tomuto zobrazení.|  
|TABLE_NAME|String|Název tabulky, který je přidružený k zobrazení. Základní tabulky.|  
|COLUMN_NAME|String|Název sloupce.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Názevsloupce|DataType|Popis|  
|----------------|--------------|-----------------|  
|název_sestavení|String|Název souboru pro sestavení.|  
|udt_name|String|Název třídy pro sestavení.|  
|version_major|Objekt|Hlavní číslo verze.|  
|version_minor|Objekt|Číslo podverze.|  
|version_build|Objekt|Číslo sestavení.|  
|version_revision|Objekt|Číslo revize.|  
|culture_info|Objekt|Informace o jazykové verzi přidružené k této UDT.|  
|veřejný_klíč|Objekt|Veřejný klíč, který používá toto sestavení.|  
|is_fixed_length|Boolean|Určuje, zda délky typu je vždy stejný jako max_length.|  
|max_length|Int16|Maximální délka typu v bajtech.|  
|Create_Date|DateTime|Datum bylo sestavení vytvořen a zaregistrován.|  
|Permission_set_desc|String|Popisný název pro oprávnění set a – úroveň zabezpečení pro sestavení.|  
  
## <a name="see-also"></a>Viz také:

- [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
