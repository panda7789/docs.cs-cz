---
title: "Kolekcemi schémat serveru SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c2f03065ee6f1292f72a33a72b1d43b1fed0c8f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-schema-collections"></a>Kolekcemi schémat serveru SQL
Zprostředkovatel dat rozhraní Microsoft .NET Framework pro SQL Server podporuje další schéma kolekce kromě běžných kolekcemi schémat. Schéma kolekce mírně lišit podle verze systému SQL Server, kterou používáte. Pokud chcete určit seznam podporovaných schématu kolekcí, volání **GetSchema** metoda bez argumentů nebo názvem schématu kolekce "MetaDataCollections". Tato možnost vrátí <xref:System.Data.DataTable> seznam podporovaných schéma kolekce, počet omezení, které každý podporují a počet identifikátor částí, které používají.  
  
## <a name="databases"></a>Databáze  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|Název databáze database_name|String|Název databáze.|  
|DBID|Int16|ID databáze.|  
|create_date|DateTime|Datum vytvoření databáze.|  
  
## <a name="foreign-keys"></a>Cizí klíče  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|String|Katalog omezení patří.|  
|CONSTRAINT_SCHEMA|String|Schéma, které obsahuje omezení.|  
|CONSTRAINT_NAME|String|Jméno.|  
|TABLE_CATALOG|String|Název omezení tabulky je součástí.|  
|TABLE_SCHEMA|String|Schéma, který obsahuje tabulky.|  
|TABLE_NAME|String|Název tabulky|  
|CONSTRAINT_TYPE|String|Typ omezení. Je povolen pouze "cizí klíč".|  
|IS_DEFERRABLE|String|Určuje, zda je deferrable omezení. Vrátí číslo.|  
|INITIALLY_DEFERRED|String|Určuje, jestli je původně deferrable omezení. Vrátí číslo.|  
  
## <a name="indexes"></a>Indexy  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, který patří index.|  
|constraint_schema|String|Schéma, které obsahuje index.|  
|constraint_name|String|Název indexu.|  
|TABLE_CATALOG|String|Název tabulky indexu je přidružen.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku index je přidružen.|  
|TABLE_NAME|String|Název tabulky.|  
|index_name|String|Název indexu.|  
  
### <a name="indexes-sql-server-2008"></a>Indexy (SQL Server 2008)  
 Od verze rozhraní .NET Framework verze 3.5 SP1 a SQL Server 2008, následující sloupce jsou přidané do kolekce schémat indexů pro podporu nových typů prostorových filestream a zhuštěné sloupce. Tyto sloupce nejsou podporovány v dřívějších verzích rozhraní .NET Framework a SQL Server.  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|type_desc|String|Typ indexu bude jeden z následujících akcí:<br /><br /> -HEAP<br />-CLUSTERU<br />-NECLUSTEROVANÝ<br />– XML<br />-PROSTOROVÝCH|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, který patří index.|  
|constraint_schema|String|Schéma, které obsahuje index.|  
|constraint_name|String|Název indexu.|  
|TABLE_CATALOG|String|Název tabulky indexu je přidružen.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku index je přidružen.|  
|TABLE_NAME|String|Název tabulky.|  
|COLUMN_NAME|String|Název sloupce indexu je přidružen.|  
|ordinal_position|Int32|Pořadové číslo pozice sloupce.|  
|Typ_klíče.|Byte|Typ objektu.|  
|index_name|String|Název indexu.|  
  
## <a name="procedures"></a>Procedury  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Konkrétní název katalogu.|  
|SPECIFIC_SCHEMA|String|Konkrétní název schématu.|  
|SPECIFIC_NAME|String|Konkrétní název katalogu.|  
|ROUTINE_CATALOG|String|Katalog uložené procedury patří.|  
|ROUTINE_SCHEMA|String|Schéma, které obsahuje uložené procedury.|  
|ROUTINE_NAME|String|Název uložené procedury.|  
|ROUTINE_TYPE|String|Vrátí postup pro uložené procedury a funkce pro funkce.|  
|VYTVOŘIT|DateTime|Čas vytvoření procesu.|  
|LAST_ALTERED|DateTime|Čas poslední postup byla změněna.|  
  
## <a name="procedure-parameters"></a>Parametry procedur  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Název procedury, pro kterou je tento parametr katalogu.|  
|SPECIFIC_SCHEMA|String|Schéma, který obsahuje postup, pro kterou je tento parametr součástí.|  
|SPECIFIC_NAME|String|Název procedury, pro kterou je tento parametr součástí.|  
|ORDINAL_POSITION|Int32|Pořadová čísla parametr začínajícím hodnotou 1. Pro návratová hodnota procedury Toto je 0.|  
|PARAMETER_MODE|String|Vrátí v případě vstupní parametr, zda výstupní parametr a INOUT Pokud vstupní/výstupní parametr.|  
|IS_RESULT|String|Vrátí Ano, pokud určuje výsledek v postupu, který je funkce. Jinak vrátí číslo.|  
|AS_LOCATOR|String|Vrátí hodnotu Ano, pokud deklarovaný jako lokátoru. Jinak vrátí číslo.|  
|PARAMETER_NAME|String|Název parametru Hodnota NULL, pokud to odpovídá návratovou hodnotu funkce.|  
|DATA_TYPE|String|Poskytnuté systémem datového typu.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maximální délka ve znacích binary nebo znak datové typy. V opačném případě vrátí hodnotu NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maximální délka v bajtech binary nebo znak datové typy. V opačném případě vrátí hodnotu NULL.|  
|COLLATION_CATALOG|String|Název katalogu kolaci parametru. Pokud není jedním z těchto typů znaků, vrátí hodnotu NULL.|  
|COLLATION_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|COLLATION_NAME|String|Název kolace parametru. Pokud není jedním z těchto typů znaků, vrátí hodnotu NULL.|  
|CHARACTER_SET_CATALOG|String|Název katalogu znaku nastavení parametru. Pokud není jedním z těchto typů znaků, vrátí hodnotu NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Název znakové sady parametru. Pokud není jedním z těchto typů znaků, vrátí hodnotu NULL.|  
|NUMERIC_PRECISION|Byte|Přesnost přibližnou číselná data, přesný číselný datový, data celé číslo nebo peněžní data. V opačném případě vrátí hodnotu NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Chcete-li základ přesností – přibližnou číselná data, přesný číselný datový, celočíselných dat nebo peněžní data. V opačném případě vrátí hodnotu NULL.|  
|NUMERIC_SCALE|Int32|Měřítko přibližnou číselná data, přesný číselný datový, data celé číslo nebo peněžní data. V opačném případě vrátí hodnotu NULL.|  
|DATETIME_PRECISION|Int16|Přesnost v zlomků sekund, je-li parametr typ datetime nebo smalldatetime. V opačném případě vrátí hodnotu NULL.|  
|INTERVAL_TYPE|String|HODNOTU NULL. Vyhrazená pro budoucí použití nástrojem systému SQL Server.|  
|INTERVAL_PRECISION|Int16|HODNOTU NULL. Vyhrazená pro budoucí použití nástrojem systému SQL Server.|  
  
## <a name="tables"></a>Tabulky  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku.|  
|TABLE_NAME|String|Název tabulky.|  
|TABLE_TYPE|String|Typ tabulky. Může být zobrazení nebo základní tabulky.|  
  
## <a name="columns"></a>Sloupce  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku.|  
|TABLE_NAME|String|Název tabulky.|  
|COLUMN_NAME|String|Název sloupce.|  
|ORDINAL_POSITION|Int32|Identifikační číslo sloupce.|  
|COLUMN_DEFAULT|String|Výchozí hodnota sloupce|  
|IS_NULLABLE|String|Možnost použití hodnoty NULL sloupce. Pokud v tomto sloupci umožňuje hodnotu NULL, vrátí se v tomto sloupci Ano. Jinak Ne je vrácen.|  
|DATA_TYPE|String|Poskytnuté systémem datového typu.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7|Maximální délka ve znacích pro binární data, data znak nebo textových a obrázkových data. V opačném případě bude vrácena hodnota NULL.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|Maximální délka v bajtech pro binární data, data znak nebo textových a obrázkových data. V opačném případě bude vrácena hodnota NULL.|  
|NUMERIC_PRECISION|Bajt bez znaménka|Přesnost přibližnou číselná data, přesný číselný datový, data celé číslo nebo peněžní data. V opačném případě bude vrácena hodnota NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Chcete-li základ přesností – přibližnou číselná data, přesný číselný datový, celočíselných dat nebo peněžní data. V opačném případě bude vrácena hodnota NULL.|  
|NUMERIC_SCALE|Int32|Měřítko přibližnou číselná data, přesný číselný datový, data celé číslo nebo peněžní data. V opačném případě bude vrácena hodnota NULL.|  
|DATETIME_PRECISION|Int16|Podtypu kód pro SQL 92 interval datové typy a data a času. Pro jiné datové typy vrátí se hodnota NULL.|  
|CHARACTER_SET_CATALOG|String|Hlavní server vrátí, pokud je sloupec textová data nebo textová data, která určuje databázi, ve kterém se nachází, znaková sada typu. V opačném případě bude vrácena hodnota NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Zadejte jedinečný název pro znak nastavit, pokud v tomto sloupci textová data nebo text data vrátí. V opačném případě bude vrácena hodnota NULL.|  
|COLLATION_CATALOG|String|Hlavní server vrátí, pokud je sloupec textová data nebo textová data, která určuje databázi, ve kterém je definovaný kolace, typu. V tomto sloupci, jinak hodnota je NULL.|  
  
### <a name="columns-sql-server-2008"></a>Sloupce (SQL Server 2008)  
 Od verze rozhraní .NET Framework verze 3.5 SP1 a SQL Server 2008, následující sloupce jsou přidané do kolekce schémat sloupců pro podporu nových typů prostorových filestream a zhuštěné sloupce. Tyto sloupce nejsou podporovány v dřívějších verzích rozhraní .NET Framework a SQL Server.  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|String|Ano, pokud sloupec obsahuje atribut FILESTREAM.<br /><br /> Ne, pokud sloupec neobsahuje atribut FILESTREAM.|  
|IS_SPARSE|String|Ano, pokud je sloupec zhuštěný sloupec.<br /><br /> Ne, pokud sloupec není zhuštěný sloupec.|  
|IS_COLUMN_SET|String|Ano, pokud sloupec je sloupec sady sloupců.<br /><br /> Ne, pokud sloupec není sloupec sady sloupců.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 Od verze rozhraní .NET Framework verze 3.5 SP1 a SQL Server 2008, přidala se kolekce schémat AllColumns pro podporu zhuštěné sloupce. AllColumns není podporované v dřívějších verzích rozhraní .NET Framework a SQL Server.  
  
 AllColumns má stejná omezení a výsledný DataTable schématu jako kolekce schémat sloupců. Jediným rozdílem je, že AllColumns obsahuje sloupec sady sloupců, které nejsou zahrnuty v kolekci schémat sloupců. Následující tabulka popisuje tyto sloupce.  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku.|  
|TABLE_NAME|String|Název tabulky.|  
|COLUMN_NAME|String|Název sloupce.|  
|ORDINAL_POSITION|Int32|Identifikační číslo sloupce.|  
|COLUMN_DEFAULT|String|Výchozí hodnota sloupce|  
|IS_NULLABLE|String|Možnost použití hodnoty NULL sloupce. Pokud v tomto sloupci umožňuje hodnotu NULL, vrátí se v tomto sloupci Ano. Jinak Ne je vrácen.|  
|DATA_TYPE|String|Poskytnuté systémem datového typu.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maximální délka ve znacích pro binární data, data znak nebo textových a obrázkových data. V opačném případě bude vrácena hodnota NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maximální délka v bajtech pro binární data, data znak nebo textových a obrázkových data. V opačném případě bude vrácena hodnota NULL.|  
|NUMERIC_PRECISION|Bajt bez znaménka|Přesnost přibližnou číselná data, přesný číselný datový, data celé číslo nebo peněžní data. V opačném případě bude vrácena hodnota NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Chcete-li základ přesností – přibližnou číselná data, přesný číselný datový, celočíselných dat nebo peněžní data. V opačném případě bude vrácena hodnota NULL.|  
|NUMERIC_SCALE|Int32|Měřítko přibližnou číselná data, přesný číselný datový, data celé číslo nebo peněžní data. V opačném případě bude vrácena hodnota NULL.|  
|DATETIME_PRECISION|Int16|Podtypu kód pro SQL 92 interval datové typy a data a času. Pro jiné datové typy vrátí se hodnota NULL.|  
|CHARACTER_SET_CATALOG|String|Hlavní server vrátí, pokud je sloupec textová data nebo textová data, která určuje databázi, ve kterém se nachází, znaková sada typu. V opačném případě bude vrácena hodnota NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Zadejte jedinečný název pro znak nastavit, pokud v tomto sloupci textová data nebo text data vrátí. V opačném případě bude vrácena hodnota NULL.|  
|COLLATION_CATALOG|String|Hlavní server vrátí, pokud je sloupec textová data nebo textová data, která určuje databázi, ve kterém je definovaný kolace, typu. V tomto sloupci, jinak hodnota je NULL.|  
|IS_FILESTREAM|String|Ano, pokud sloupec obsahuje atribut FILESTREAM.<br /><br /> Ne, pokud sloupec neobsahuje atribut FILESTREAM.|  
|IS_SPARSE|String|Ano, pokud je sloupec zhuštěný sloupec.<br /><br /> Ne, pokud sloupec není zhuštěný sloupec.|  
|IS_COLUMN_SET|String|Ano, pokud sloupec je sloupec sady sloupců.<br /><br /> Ne, pokud sloupec není sloupec sady sloupců.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 Od verze rozhraní .NET Framework verze 3.5 SP1 a SQL Server 2008, přidala se kolekce schémat ColumnSetColumns pro podporu zhuštěné sloupce. ColumnSetColumns není podporované v dřívějších verzích rozhraní .NET Framework a SQL Server. Kolekce schémat ColumnSetColumns vrací schéma pro všechny sloupce v sadě sloupců. Následující tabulka popisuje tyto sloupce.  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku.|  
|TABLE_NAME|String|Název tabulky.|  
|COLUMN_NAME|String|Název sloupce.|  
|ORDINAL_POSITION|Int32|Identifikační číslo sloupce.|  
|COLUMN_DEFAULT|String|Výchozí hodnota sloupce|  
|IS_NULLABLE|String|Možnost použití hodnoty NULL sloupce. Pokud v tomto sloupci umožňuje hodnotu NULL, vrátí se v tomto sloupci Ano. Jinak Ne je vrácen.|  
|DATA_TYPE|String|Poskytnuté systémem datového typu.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maximální délka ve znacích pro binární data, data znak nebo textových a obrázkových data. V opačném případě bude vrácena hodnota NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maximální délka v bajtech pro binární data, data znak nebo textových a obrázkových data. V opačném případě bude vrácena hodnota NULL.|  
|NUMERIC_PRECISION|Bajt bez znaménka|Přesnost přibližnou číselná data, přesný číselný datový, data celé číslo nebo peněžní data. V opačném případě bude vrácena hodnota NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Chcete-li základ přesností – přibližnou číselná data, přesný číselný datový, celočíselných dat nebo peněžní data. V opačném případě bude vrácena hodnota NULL.|  
|NUMERIC_SCALE|Int32|Měřítko přibližnou číselná data, přesný číselný datový, data celé číslo nebo peněžní data. V opačném případě bude vrácena hodnota NULL.|  
|DATETIME_PRECISION|Int16|Podtypu kód pro SQL 92 interval datové typy a data a času. Pro jiné datové typy vrátí se hodnota NULL.|  
|CHARACTER_SET_CATALOG|String|Hlavní server vrátí, pokud je sloupec textová data nebo textová data, která určuje databázi, ve kterém se nachází, znaková sada typu. V opačném případě bude vrácena hodnota NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Zadejte jedinečný název pro znak nastavit, pokud v tomto sloupci textová data nebo text data vrátí. V opačném případě bude vrácena hodnota NULL.|  
|COLLATION_CATALOG|String|Hlavní server vrátí, pokud je sloupec textová data nebo textová data, která určuje databázi, ve kterém je definovaný kolace, typu. V tomto sloupci, jinak hodnota je NULL.|  
|IS_FILESTREAM|String|Ano, pokud sloupec obsahuje atribut FILESTREAM.<br /><br /> Ne, pokud sloupec neobsahuje atribut FILESTREAM.|  
|IS_SPARSE|String|Ano, pokud je sloupec zhuštěný sloupec.<br /><br /> Ne, pokud sloupec není zhuštěný sloupec.|  
|IS_COLUMN_SET|String|Ano, pokud sloupec je sloupec sady sloupců.<br /><br /> Ne, pokud sloupec není sloupec sady sloupců.|  
  
## <a name="users"></a>Uživatelé  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|UID|Int16|ID uživatele, v této databázi jedinečné. 1 je vlastník databáze.|  
|uživatelské_jméno|String|Uživatelské jméno nebo název skupiny, v této databázi jedinečné.|  
|CREATEDATE formát|DateTime|Datum, kdy byla přidána k účtu.|  
|updatedate|DateTime|Datum, kdy byl naposled změněn účet.|  
  
## <a name="views"></a>zobrazení  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog zobrazení.|  
|TABLE_SCHEMA|String|Schéma, která obsahuje zobrazení.|  
|TABLE_NAME|String|Název zobrazení.|  
|CHECK_OPTION|String|Typ možností kontroly. Pokud původní zobrazení byla vytvořena pomocí WITH CHECK OPTION, je CASCADE. Jinak se vrátí NONE.|  
|IS_UPDATABLE|String|Určuje, zda je zobrazení aktualizovat. Vždy vrátí hodnotu Ne.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|String|Katalog zobrazení.|  
|VIEW_SCHEMA|String|Schéma, která obsahuje zobrazení.|  
|VIEW_NAME|String|Název zobrazení.|  
|TABLE_CATALOG|String|Katalog tabulky, která je přidružená k tomuto zobrazení.|  
|TABLE_SCHEMA|String|Schéma, který obsahuje tabulky, která je přidružená k tomuto zobrazení.|  
|TABLE_NAME|String|Název tabulky, který je přidružený k zobrazení. Základní tabulka.|  
|COLUMN_NAME|String|Název sloupce.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|assembly_name|String|Název souboru pro sestavení.|  
|udt_name|String|Název třídy pro sestavení.|  
|version_major|Objekt|Hlavní číslo verze.|  
|version_minor|Objekt|Číslo podverze.|  
|version_build|Objekt|Číslo sestavení.|  
|version_revision|Objekt|Číslo revize.|  
|culture_info|Objekt|Informace o jazykové verzi přidružené k této UDT.|  
|public_key|Objekt|Veřejný klíč používaný toto sestavení.|  
|is_fixed_length|Boolean|Určuje, zda délka typu je vždy stejný jako max_length.|  
|max_length|Int16|Maximální délka typu v bajtech.|  
|Create_Date|DateTime|Datum sestavení byl vytvořen zaregistrován.|  
|Permission_set_desc|String|Popisný název oprávnění set nebo-úroveň zabezpečení pro sestavení.|  
  
## <a name="see-also"></a>Viz také  
 [Načítání informací o schématu databáze](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
