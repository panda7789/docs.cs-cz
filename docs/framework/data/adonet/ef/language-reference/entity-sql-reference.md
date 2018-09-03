---
title: Reference k Entity SQL
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: ae0aec999d30d099467be690b8920d1413b564f0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43487416"
---
# <a name="entity-sql-reference"></a>Reference k Entity SQL

Tento oddíl obsahuje články referenční dokumentace jazyka Entity SQL. Tento článek shrnuje a skupiny operátorů Entity SQL podle kategorie.

## <a name="arithmetic-operators"></a>Aritmetické operátory

Aritmetické operátory provádění matematických operací na dvou výrazů jeden nebo více číselné datové typy. V následující tabulce jsou uvedeny Entity SQL aritmetické operátory:

|Operátor|Použití|
|--------------|---------|
|[+ (Přičíst)](add.md)|Přidání.|
|[/ (Dělit)](divide-entity-sql.md)|Dělení.|
|[% (Modulo)](modulo-entity-sql.md)|Vrátí zbytek dělení.|
|[* (Násobit)](multiply-entity-sql.md)|Násobení.|
|[- (Záporné)](negative-entity-sql.md)|Negace.|
|[- (Odečíst)](subtract-entity-sql.md)|Odčítání.|

## <a name="canonical-functions"></a>Kanonické funkce

Kanonické funkce jsou podporovány všechny poskytovatele dat a mohou využívat všechny dotazy technologie. V následující tabulce jsou uvedeny kanonické funkce:

|Funkce|Typ|
|--------------|----------|
|[Kanonické funkce agregace Entity SQL](aggregate-canonical-functions.md)|Tento článek popisuje agregační kanonické funkce Entity SQL.|
|[Matematické kanonické funkce](math-canonical-functions.md)|Tento článek popisuje matematické kanonické funkce Entity SQL.|
|[Řetězcové kanonické funkce](string-canonical-functions.md)|Tento článek popisuje řetězcové kanonické funkce Entity SQL.|
|[Kanonické funkce pro datum a čas](date-and-time-canonical-functions.md)|Tento článek popisuje data a času kanonické funkce Entity SQL.|
|[Bitové kanonické funkce](bitwise-canonical-functions.md)|Tento článek popisuje bitové kanonické funkce Entity SQL.|
|[Jiné kanonické funkce](other-canonical-functions.md)|Tento článek popisuje funkce nejsou klasifikovány jako bitové operace, datum a čas, řetězec, matematických výpočtů nebo agregace.|

## <a name="comparison-operators"></a>Operátory porovnání

Operátory porovnání jsou definovány pro následující typy: `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time` , `DateTimeOffset`. Propagace typu implicitní dochází operandů před použitím operátoru porovnání. Operátory porovnání vždy zobrazit logické hodnoty. Nejméně jeden z operandů při `null`, výsledkem je `null`.

Rovnost a nerovnost jsou definovány pro libovolný typ objektu, který má identitu, například `Boolean` typu. Které nejsou primitivní objekty s identitou jsou považovány za shodné, pokud uživatelé sdílejí stejnou identitu. V následující tabulce jsou uvedeny operátory porovnání Entity SQL:

|Operátor|Popis|
|--------------|-----------------|
|[= (Je rovno)](equals-entity-sql.md)|Porovná rovnost dvou výrazů.|
|[> (Větší než)](greater-than-entity-sql.md)|Porovná dva výrazy k určení, zda levý výraz má hodnotu větší než pravý výraz.|
|[>= (Větší než nebo rovno)](greater-than-or-equal-to-entity-sql.md)|Porovná dva výrazy k určení, zda levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz.|
|[JE \[NENÍ\] NULL](isnull-entity-sql.md)|Určuje, zda výraz dotazu je null.|
|[< (Méně než)](less-than-entity-sql.md)|Porovná dva výrazy k určení, zda levý výraz má hodnotu menší, než pravý výraz.|
|[<= (Méně než nebo rovno)](less-than-or-equal-to-entity-sql.md)|Porovná dva výrazy k určení, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.|
|[\[NENÍ\] BETWEEN](between-entity-sql.md)|Určuje, zda výraz výsledkem je hodnota v zadaném rozsahu.|
|[\!= (Nerovná se)](not-equal-to-entity-sql.md)|Porovná dva výrazy k určení, zda levý výraz není roven pravý výraz.|
|[\[NENÍ\] JAKO](like-entity-sql.md)|Určuje, zda řetězec konkrétní znak odpovídá zadanému vzoru.|

## <a name="logical-and-case-expression-operators"></a>Výraz case a logické operátory

Logické operátory testování pravdivost podmínku. Výraz CASE vyhodnotí sadu logických výrazů k určení výsledků. V následující tabulce jsou uvedeny operátory případů a logických výrazů:

|Operátor|Popis|
|--------------|-----------------|
|[& & (Logický operátor a)](and-entity-sql.md)|Logickým operátorem a.|
|[\! (Logický operátor NOT)](not-entity-sql.md)|Logický operátor NOT.|
|[&#124;&#124;(Logický operátor OR)](or-entity-sql.md)|Logický operátor OR.|
|[CASE](case-entity-sql.md)|Vyhodnotí sadu logických výrazů k určení výsledků.|
|[THEN](then-entity-sql.md)|Výsledek [při](https://msdn.microsoft.com/library/6233fe9f-00b0-460e-8372-64e138a5f998) klauzuli, pokud je vyhodnocen jako true.|

## <a name="query-operators"></a>Operátory dotazu

Operátory dotazu se používají k definování výrazy dotazů, které nevracejí entity data. V následující tabulce jsou uvedeny operátory dotazu:

|Operátor|Použití|
|--------------|---------|
|[FROM](from-entity-sql.md)|Určuje kolekci, která se používá v [vyberte](select-entity-sql.md) příkazy.|
|[GROUP BY](group-by-entity-sql.md)|Určuje skupiny, do které objekty, které jsou vrácené dotazem ([vyberte](select-entity-sql.md)) výrazu mají být umístěny.|
|[GroupPartition](grouppartition-entity-sql.md)|Vrátí kolekci hodnot argumentů, plánované vypnutí oddílu skupiny, ke kterému se vztahuje agregace.|
|[HAVING](having-entity-sql.md)|Určuje podmínku hledání pro skupinu nebo agregace.|
|[LIMIT](limit-entity-sql.md)|Použít s [klauzule ORDER BY](order-by-entity-sql.md) klauzule, která provádí fyzické stránkování.|
|[ORDER BY](order-by-entity-sql.md)|Určuje, který se používá u objektů, které jsou vráceny v pořadí řazení [vyberte](select-entity-sql.md) příkazu.|
|[SELECT](select-entity-sql.md)|Určuje prvky v projekci, které jsou vrácené dotazem.|
|[SKIP](skip-entity-sql.md)|Použít s [klauzule ORDER BY](order-by-entity-sql.md) klauzule, která provádí fyzické stránkování.|
|[TOP](top-entity-sql.md)|Určuje, že bude vrácen pouze první sada řádků z výsledku dotazu.|
|[WHERE](where-entity-sql.md)|Podmíněně filtruje data, která je vrácena dotazem.|

## <a name="reference-operators"></a>Odkazovací operátory

Odkaz je logický ukazatel (cizí klíč) na konkrétní entitu v sadě konkrétní entity. Entita SQL podporuje následující operátory sestavit, dekonstruovat a procházejte odkazy:

|Operátor|Použití|
|--------------|---------|
|[CREATEREF](createref-entity-sql.md)|Vytvoří odkazy na entity v sadě entit.|
|[DEREF](deref-entity-sql.md)|Přístupů přes ukazatel referenčními hodnotami a vytváří výsledek, který přístup přes ukazatel.|
|[KEY](key-entity-sql.md)|Extrahuje klíč odkazu nebo výrazu entity.|
|[NAVIGATE](navigate-entity-sql.md)|Umožňuje přejít nad vztah z jedné entitě typu na jiný|
|[REF](ref-entity-sql.md)|Vrátí odkaz na instanci entity.|

## <a name="set-operators"></a>Množinové operátory

Entita SQL poskytuje různé operace výkonnou sadu. Jedná se o sadu operátorů operátorů jazyka Transact-SQL, například UNION, INTERSECT, EXCEPT, podobně jako a EXISTS. Entita SQL také podporuje operátory pro odstranění duplicit (SET), členství v testování (IN) a spojení (spojení). V následující tabulce jsou uvedeny operátory set Entity SQL:

|Operátor|Použití|
|--------------|---------|
|[ANYELEMENT](anyelement-entity-sql.md)|Extrahuje element z kolekce s více hodnotami.|
|[EXCEPT](except-entity-sql.md)|Vrátí kolekci všech jedinečných hodnot z výrazu dotazu k levému operandu EXCEPT, která nejsou také vrácen z výrazu dotazu napravo od EXCEPT operand.|
|[\[NENÍ\] EXISTS](exists-entity-sql.md)|Určuje, zda je kolekce prázdná.|
|[FLATTEN](flatten-entity-sql.md)|Převede kolekci kolekcí plochá kolekce.|
|[\[NENÍ\] INDIE](in-entity-sql.md)|Určuje, zda hodnota odpovídá libovolné hodnotě v kolekci.|
|[INTERSECT](intersect-entity-sql.md)|Vrátí kolekci všech jedinečných hodnot, které jsou vráceny ve výrazech dotazů na levé straně a pravé straně INTERSECT operandu.|
|[OVERLAPS](overlaps-entity-sql.md)|Určuje, jestli dvě kolekce mají společné prvky.|
|[SET](set-entity-sql.md)|Slouží k převodu kolekce objektů do sady podle získávání novou kolekci s odstraněnými všechny duplicitní prvky.|
|[UNION](union-entity-sql.md)|Kombinuje výsledky ze dvou nebo více dotazů do jedné kolekce.|

## <a name="type-operators"></a>Operátory typu

Entita SQL poskytuje operace, které umožňují typ výrazu (hodnota) vytvořen, dotazovat a manipulovat. V následující tabulce jsou uvedeny operátory, které se používají k práci s typy:

|Operátor|Použití|
|--------------|---------|
|[CAST](cast-entity-sql.md)|Převede výraz jednoho datového typu na jiný.|
|[COLLECTION](collection-entity-sql.md)|Používané [funkce](function-entity-sql.md) operace pro deklaraci kolekci typů entit nebo komplexních typů.|
|[JE \[NENÍ\] OF](isof-entity-sql.md)|Určuje, zda je typ výrazu zadaný typ nebo některý z jeho podtypy.|
|[OFTYPE](oftype-entity-sql.md)|Vrátí kolekci objektů z výrazu dotazu, který je určitého typu.|
|[Konstruktor pojmenovaného typu](named-type-constructor-entity-sql.md)|Použít k vytvoření instancí typů entit nebo komplexních typů.|
|[MULTISET](multiset-entity-sql.md)|Vytvoří instanci multisady ze seznamu hodnot.|
|[ROW](row-entity-sql.md)|Sestaví anonymní, strukturálně typy záznamů z jedné nebo více hodnot.|
|[TREAT](treat-entity-sql.md)|Zpracovává konkrétní základního typu objektu jako objekt zadaného typu odvozené.|

## <a name="other-operators"></a>Ostatní operátory

V následující tabulce jsou uvedeny ostatní operátory Entity SQL:

|Operátor|Použití|
|--------------|---------|
|[+ (Zřetězení řetězců)](string-concatenation-entity-sql.md)|Použít ke zřetězení řetězců v Entity SQL.|
|[. (Přístup ke členu)](member-access-entity-sql.md)|Používá pro přístup k hodnotě vlastnosti nebo pole instance typu strukturální koncepčního modelu.|
|[– (komentář)](comment-entity-sql.md)|Zahrnutí komentářů Entity SQL.|
|[FUNCTION](function-entity-sql.md)|Definuje vložené funkce, které mohou být provedeny v dotazu Entity SQL.|

## <a name="see-also"></a>Viz také:

[Jazyk Entity SQL](entity-sql-language.md)
