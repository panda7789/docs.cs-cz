---
title: Kolekce schémat SQL Serveru
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: 0f65bbf2534eb7167baacb1405a8ce6e9769c23f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794330"
---
# <a name="sql-server-schema-collections"></a>Kolekce schémat SQL Serveru
Microsoft .NET Framework Zprostředkovatel dat pro SQL Server podporuje kromě běžných kolekcí schémat i další kolekce schémat. Kolekce schémat se mírně liší podle verze SQL Server, kterou používáte. Chcete-li určit seznam podporovaných kolekcí schémat, zavolejte metodu **GetSchema** bez argumentů nebo s názvem kolekce schématu "MetaDataCollections". Tato akce vrátí <xref:System.Data.DataTable> seznam podporovaných kolekcí schémat, počet omezení, která jednotlivé požadavky podporují, a počet částí identifikátorů, které používají.  
  
## <a name="databases"></a>Databáze  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|název_databáze|String|Název databáze.|  
|dbid|Int16|ID databáze.|  
|create_date|DateTime|Datum vytvoření databáze|  
  
## <a name="foreign-keys"></a>Cizí klíče  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|String|Katalog, ke kterému omezení patří|  
|CONSTRAINT_SCHEMA|String|Schéma, které obsahuje omezení|  
|CONSTRAINT_NAME|String|Jméno.|  
|TABLE_CATALOG|String|Omezení názvu tabulky je součástí.|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku|  
|TABLE_NAME|String|Název tabulky|  
|CONSTRAINT_TYPE|String|Typ omezení Je povolený jenom "cizí klíč".|  
|IS_DEFERRABLE|String|Určuje, zda je omezení odloženo. Vrátí hodnotu NO.|  
|INITIALLY_DEFERRED|String|Určuje, zda je omezení zpočátku odvoditelné. Vrátí hodnotu NO.|  
  
## <a name="indexes"></a>Indexy  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, ke kterému patří index|  
|constraint_schema|String|Schéma, které obsahuje index.|  
|constraint_name|String|Název indexu.|  
|table_catalog|String|Název tabulky, ke které je index přidružen.|  
|table_schema|String|Schéma obsahující tabulku, ke které je index přidružen.|  
|TABLE_NAME|String|Název tabulky|  
|index_name|String|Název indexu.|  
  
### <a name="indexes-sql-server-2008"></a>Indexes (SQL Server 2008)  
 Počínaje verzí .NET Framework 3,5 SP1 a SQL Server 2008 byly do kolekce schémat indexů přidány následující sloupce pro podporu nových prostorových typů, FILESTREAM a zhuštěných sloupců. Tyto sloupce nejsou podporované v dřívějších verzích .NET Framework a SQL Server.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|type_desc|String|Typ indexu bude jeden z následujících:<br /><br /> – HALDA<br />-CLUSTERED<br />– NECLUSTEROVANÝ<br />– XML<br />– PROSTOROVÁ|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Katalog, ke kterému patří index|  
|constraint_schema|String|Schéma, které obsahuje index.|  
|constraint_name|String|Název indexu.|  
|table_catalog|String|Název tabulky, ke které je index přidružen.|  
|table_schema|String|Schéma obsahující tabulku, ke které je index přidružen.|  
|TABLE_NAME|String|Název tabulky|  
|column_name|String|Název sloupce, ke kterému je index přidružen.|  
|ordinal_position|Int32|Ordinální pozice sloupce|  
|KeyType|Byte|Typ objektu.|  
|index_name|String|Název indexu.|  
  
## <a name="procedures"></a>Procedury  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Konkrétní název katalogu.|  
|SPECIFIC_SCHEMA|String|Konkrétní název schématu.|  
|SPECIFIC_NAME|String|Konkrétní název katalogu.|  
|ROUTINE_CATALOG|String|Katalog, do kterého uložená procedura patří|  
|ROUTINE_SCHEMA|String|Schéma, které obsahuje uloženou proceduru.|  
|ROUTINE_NAME|String|Název uložené procedury|  
|ROUTINE_TYPE|String|Vrátí PROCEDURu pro uložené procedury a funkce pro funkce.|  
|VYTVÁŘEJÍ|DateTime|Čas, kdy byla procedura vytvořena.|  
|LAST_ALTERED|DateTime|Čas poslední změny procedury.|  
  
## <a name="procedure-parameters"></a>Parametry procedury  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Název katalogu pro proceduru, pro kterou je toto parametr.|  
|SPECIFIC_SCHEMA|String|Schéma, které obsahuje proceduru, pro kterou je tento parametr součástí.|  
|SPECIFIC_NAME|String|Název procedury, pro kterou je tento parametr součástí.|  
|ORDINAL_POSITION|Int32|Ordinální pozice parametru začínajícího hodnotou 1. Pro návratovou hodnotu procedury je to 0.|  
|PARAMETER_MODE|String|Vrátí v případě, že vstupní parametr, OUT, pokud je výstupní parametr, a INOUT, pokud vstupní/výstupní parametr.|  
|IS_RESULT|String|Vrátí hodnotu Ano, pokud indikuje výsledek procedury, která je funkcí. V opačném případě vrátí hodnotu ne.|  
|AS_LOCATOR|String|Vrátí hodnotu Ano, pokud je deklarována jako lokátor. V opačném případě vrátí hodnotu ne.|  
|PARAMETER_NAME|String|Název parametru NULL, pokud to odpovídá návratové hodnotě funkce.|  
|DATA_TYPE|String|Datový typ zadaný systémem.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maximální délka znaků pro binární nebo znakové datové typy. V opačném případě vrátí hodnotu NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maximální délka v bajtech pro binární nebo znakové datové typy. V opačném případě vrátí hodnotu NULL.|  
|COLLATION_CATALOG|String|Název katalogu kolace parametru Pokud není jeden z typů znaků, vrátí hodnotu NULL.|  
|COLLATION_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|COLLATION_NAME|String|Název kolace parametru. Pokud není jeden z typů znaků, vrátí hodnotu NULL.|  
|CHARACTER_SET_CATALOG|String|Název katalogu znakové sady parametru Pokud není jeden z typů znaků, vrátí hodnotu NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Název znakové sady parametru Pokud není jeden z typů znaků, vrátí hodnotu NULL.|  
|NUMERIC_PRECISION|Byte|Přesnost přibližných číselných dat, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě vrátí hodnotu NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Základ hodnoty pro Přibližná číselná data, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě vrátí hodnotu NULL.|  
|NUMERIC_SCALE|Int32|Škálujte Přibližná číselná data, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě vrátí hodnotu NULL.|  
|DATETIME_PRECISION|Int16|Přesnost za zlomky sekund, je-li typ parametru typu DateTime nebo smalldatetime. V opačném případě vrátí hodnotu NULL.|  
|INTERVAL_TYPE|String|PLATNOST. Vyhrazeno pro budoucí použití SQL Server.|  
|INTERVAL_PRECISION|Int16|PLATNOST. Vyhrazeno pro budoucí použití SQL Server.|  
  
## <a name="tables"></a>Tabulky  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku|  
|TABLE_NAME|String|Název tabulky|  
|TABLE_TYPE|String|Typ tabulky Může být zobrazení nebo základní tabulka.|  
  
## <a name="columns"></a>Sloupce  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku|  
|TABLE_NAME|String|Název tabulky|  
|COLUMN_NAME|String|Název sloupce|  
|ORDINAL_POSITION|Int32|Identifikační číslo sloupce|  
|COLUMN_DEFAULT|String|Výchozí hodnota sloupce|  
|IS_NULLABLE|String|Hodnota null sloupce Pokud tento sloupec povoluje hodnotu NULL, vrátí tento sloupec hodnotu YES (Ano). V opačném případě se vrátí No.|  
|DATA_TYPE|String|Datový typ zadaný systémem.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7 lze|Maximální délka, ve znacích, pro binární data, znaková data nebo textová a obrazová data. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|Maximální délka, v bajtech, pro binární data, znaková data nebo textová a obrazová data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION|Bajt bez znaménka|Přesnost přibližných číselných dat, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Základ hodnoty pro Přibližná číselná data, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_SCALE|Int32|Škálujte Přibližná číselná data, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|DATETIME_PRECISION|Int16|Kód podtypu pro datové typy DateTime a v intervalu SQL-92. Pro jiné datové typy je vrácena hodnota NULL.|  
|CHARACTER_SET_CATALOG|String|Vrátí hlavní server, který označuje databázi, ve které se znaková sada nachází, pokud je sloupec znaková data nebo textový datový typ. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Vrátí jedinečný název znakové sady, pokud je tento sloupec znaková data nebo textový datový typ. V opačném případě je vrácena hodnota NULL.|  
|COLLATION_CATALOG|String|Vrátí hlavní server, který označuje databázi, ve které je kolace definovaná, pokud je sloupec znaková data nebo textový datový typ. V opačném případě je tento sloupec NULL.|  
  
### <a name="columns-sql-server-2008"></a>Columns (SQL Server 2008)  
 Počínaje verzí .NET Framework 3,5 SP1 a SQL Server 2008 byly do kolekce schémat sloupců přidány následující sloupce pro podporu nových prostorových typů, FILESTREAM a zhuštěných sloupců. Tyto sloupce nejsou podporované v dřívějších verzích .NET Framework a SQL Server.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|String|Ano, pokud má sloupec atribut FILESTREAM.<br /><br /> Ne, pokud sloupec nemá atribut FILESTREAM.|  
|IS_SPARSE|String|Ano, pokud je sloupec zhuštěným sloupcem.<br /><br /> Ne, pokud sloupec není zhuštěný sloupec.|  
|IS_COLUMN_SET|String|Ano, pokud je sloupec sada sloupců.<br /><br /> Ne, pokud sloupec není sloupcem sady sloupců.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 Počínaje verzí .NET Framework 3,5 SP1 a SQL Server 2008 byla kolekce schémat AllColumns přidána k podpoře zhuštěných sloupců. AllColumns se v dřívějších verzích .NET Framework a SQL Server nepodporuje.  
  
 AllColumns má stejná omezení a výsledné schéma DataTable jako kolekce schématu sloupců. Jediným rozdílem je, že AllColumns zahrnuje sloupce sady sloupců, které nejsou zahrnuté v kolekci schémat sloupců. Tyto sloupce jsou popsány v následující tabulce.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku|  
|TABLE_NAME|String|Název tabulky|  
|COLUMN_NAME|String|Název sloupce|  
|ORDINAL_POSITION|Int32|Identifikační číslo sloupce|  
|COLUMN_DEFAULT|String|Výchozí hodnota sloupce|  
|IS_NULLABLE|String|Hodnota null sloupce Pokud tento sloupec povoluje hodnotu NULL, vrátí tento sloupec hodnotu YES (Ano). V opačném případě se vrátí NO.|  
|DATA_TYPE|String|Datový typ zadaný systémem.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maximální délka, ve znacích, pro binární data, znaková data nebo textová a obrazová data. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maximální délka, v bajtech, pro binární data, znaková data nebo textová a obrazová data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION|Bajt bez znaménka|Přesnost přibližných číselných dat, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Základ hodnoty pro Přibližná číselná data, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_SCALE|Int32|Škálujte Přibližná číselná data, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|DATETIME_PRECISION|Int16|Kód podtypu pro datové typy DateTime a v intervalu SQL-92. Pro jiné datové typy je vrácena hodnota NULL.|  
|CHARACTER_SET_CATALOG|String|Vrátí hlavní server, který označuje databázi, ve které se znaková sada nachází, pokud je sloupec znaková data nebo textový datový typ. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Vrátí jedinečný název znakové sady, pokud je tento sloupec znaková data nebo textový datový typ. V opačném případě je vrácena hodnota NULL.|  
|COLLATION_CATALOG|String|Vrátí hlavní server, který označuje databázi, ve které je kolace definovaná, pokud je sloupec znaková data nebo textový datový typ. V opačném případě je tento sloupec NULL.|  
|IS_FILESTREAM|String|Ano, pokud má sloupec atribut FILESTREAM.<br /><br /> Ne, pokud sloupec nemá atribut FILESTREAM.|  
|IS_SPARSE|String|Ano, pokud je sloupec zhuštěným sloupcem.<br /><br /> Ne, pokud sloupec není zhuštěný sloupec.|  
|IS_COLUMN_SET|String|Ano, pokud je sloupec sada sloupců.<br /><br /> Ne, pokud sloupec není sloupcem sady sloupců.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 Počínaje verzí .NET Framework 3,5 SP1 a SQL Server 2008 byla kolekce schémat ColumnSetColumns přidána k podpoře zhuštěných sloupců. ColumnSetColumns se v dřívějších verzích .NET Framework a SQL Server nepodporuje. Kolekce schémat ColumnSetColumns vrací schéma pro všechny sloupce v sadě sloupců. Tyto sloupce jsou popsány v následující tabulce.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog tabulky|  
|TABLE_SCHEMA|String|Schéma, které obsahuje tabulku|  
|TABLE_NAME|String|Název tabulky|  
|COLUMN_NAME|String|Název sloupce|  
|ORDINAL_POSITION|Int32|Identifikační číslo sloupce|  
|COLUMN_DEFAULT|String|Výchozí hodnota sloupce|  
|IS_NULLABLE|String|Hodnota null sloupce Pokud tento sloupec povoluje hodnotu NULL, vrátí tento sloupec hodnotu YES (Ano). V opačném případě se vrátí NO.|  
|DATA_TYPE|String|Datový typ zadaný systémem.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Maximální délka, ve znacích, pro binární data, znaková data nebo textová a obrazová data. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Maximální délka, v bajtech, pro binární data, znaková data nebo textová a obrazová data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION|Bajt bez znaménka|Přesnost přibližných číselných dat, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Základ hodnoty pro Přibližná číselná data, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|NUMERIC_SCALE|Int32|Škálujte Přibližná číselná data, přesná číselná data, celočíselná data nebo peněžní data. V opačném případě je vrácena hodnota NULL.|  
|DATETIME_PRECISION|Int16|Kód podtypu pro datové typy DateTime a v intervalu SQL-92. Pro jiné datové typy je vrácena hodnota NULL.|  
|CHARACTER_SET_CATALOG|String|Vrátí hlavní server, který označuje databázi, ve které se znaková sada nachází, pokud je sloupec znaková data nebo textový datový typ. V opačném případě je vrácena hodnota NULL.|  
|CHARACTER_SET_SCHEMA|String|Vždy vrátí hodnotu NULL.|  
|CHARACTER_SET_NAME|String|Vrátí jedinečný název znakové sady, pokud je tento sloupec znaková data nebo textový datový typ. V opačném případě je vrácena hodnota NULL.|  
|COLLATION_CATALOG|String|Vrátí hlavní server, který označuje databázi, ve které je kolace definovaná, pokud je sloupec znaková data nebo textový datový typ. V opačném případě je tento sloupec NULL.|  
|IS_FILESTREAM|String|Ano, pokud má sloupec atribut FILESTREAM.<br /><br /> Ne, pokud sloupec nemá atribut FILESTREAM.|  
|IS_SPARSE|String|Ano, pokud je sloupec zhuštěným sloupcem.<br /><br /> Ne, pokud sloupec není zhuštěný sloupec.|  
|IS_COLUMN_SET|String|Ano, pokud je sloupec sada sloupců.<br /><br /> Ne, pokud sloupec není sloupcem sady sloupců.|  
  
## <a name="users"></a>Uživatelé  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|UID|Int16|ID uživatele, které je v této databázi jedinečné. 1 je vlastníkem databáze.|  
|uživatelské jméno|String|Uživatelské jméno nebo název skupiny, jedinečné v této databázi.|  
|CreateDate|DateTime|Datum, kdy se účet přidal.|  
|updatedate|DateTime|Datum poslední změny účtu|  
  
## <a name="views"></a>Zobrazení  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Katalog zobrazení|  
|TABLE_SCHEMA|String|Schéma, které obsahuje zobrazení|  
|TABLE_NAME|String|Název zobrazení|  
|CHECK_OPTION|String|Typ s možností CHECK Je KASKÁDová, pokud bylo vytvořeno původní zobrazení pomocí možnosti WITH CHECK. V opačném případě se nevrátí žádná.|  
|IS_UPDATABLE|String|Určuje, zda je zobrazení možné aktualizovat. Vždy vrátí hodnotu NO.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|String|Katalog zobrazení|  
|VIEW_SCHEMA|String|Schéma, které obsahuje zobrazení|  
|VIEW_NAME|String|Název zobrazení|  
|TABLE_CATALOG|String|Katalog tabulky, která je přidružena k tomuto zobrazení|  
|TABLE_SCHEMA|String|Schéma obsahující tabulku, která je přidružena k tomuto zobrazení.|  
|TABLE_NAME|String|Název tabulky, která je přidružena k zobrazení Základní tabulka.|  
|COLUMN_NAME|String|Název sloupce|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|assembly_name|String|Název souboru pro sestavení.|  
|udt_name|String|Název třídy pro sestavení.|  
|version_major|Objekt|Číslo hlavní verze.|  
|version_minor|Objekt|Číslo dílčí verze|  
|version_build|Objekt|Číslo buildu.|  
|version_revision|Objekt|Číslo revize|  
|culture_info|Objekt|Informace o jazykové verzi přidružené k tomuto modelu UDT.|  
|public_key|Objekt|Veřejný klíč používaný tímto sestavením.|  
|is_fixed_length|Boolean|Určuje, zda je délka typu vždy stejná jako max_length.|  
|max_length|Int16|Maximální délka typu v bajtech|  
|Create_Date|DateTime|Datum, kdy bylo sestavení vytvořeno/registrováno.|  
|Permission_set_desc|String|Popisný název pro oprávnění-sada nebo úroveň zabezpečení pro sestavení.|  
  
## <a name="see-also"></a>Viz také:

- [Načítání informací o databázovém schématu](retrieving-database-schema-information.md)
- [Přehled ADO.NET](ado-net-overview.md)
