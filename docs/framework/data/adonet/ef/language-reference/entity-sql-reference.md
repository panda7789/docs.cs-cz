---
title: Odkaz na entitu SQL
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: 79cdf35128ac35920797060b09ff2fc5999708a7
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028016"
---
# <a name="entity-sql-reference"></a>Odkaz na entitu SQL

Tato část obsahuje články odkaz Entity SQL. Tento článek shrnuje a skupiny operátory Entity SQL podle kategorie.

## <a name="arithmetic-operators"></a>Aritmetické operátory

Aritmetické operátory provádět matematické operace dvou výrazů jeden nebo více číselné datové typy. Následující tabulka uvádí aritmetické operátory Entity SQL:

|Operátor|Použití|
|--------------|---------|
|[+ (Přičíst)](add.md)|Přidání.|
|[/ (Dělit)](divide-entity-sql.md)|Dělení.|
|[% (Modulo)](modulo-entity-sql.md)|Vrátí zbytek dělení.|
|[* (Násobit)](multiply-entity-sql.md)|Násobení.|
|[- (Záporné)](negative-entity-sql.md)|Negace.|
|[- (Odečíst)](subtract-entity-sql.md)|Odčítání.|

## <a name="canonical-functions"></a>Kanonické funkce

Kanonické funkce jsou podporovány všechny zprostředkovateli dat a mohou být využívána všechny dotazování technologie. Následující tabulka uvádí kanonické funkce:

|Funkce|Typ|
|--------------|----------|
|[Funkce kanonické agregační Entity SQL](aggregate-canonical-functions.md)|Popisuje agregační funkce kanonický Entity SQL.|
|[Matematické kanonické funkce](math-canonical-functions.md)|Popisuje matematické Entity SQL kanonické funkce.|
|[Řetězcové kanonické funkce](string-canonical-functions.md)|Popisuje funkce kanonický řetězce Entity SQL.|
|[Kanonické funkce pro datum a čas](date-and-time-canonical-functions.md)|Popisuje funkce kanonický Entity SQL, data a času.|
|[Bitové kanonické funkce](bitwise-canonical-functions.md)|Popisuje bitové kanonické funkce Entity SQL.|
|[Jiné kanonické funkce](other-canonical-functions.md)|Popisuje funkce není klasifikovaný bitové, datum a čas, řetězec, matematické nebo agregace.|

## <a name="comparison-operators"></a>Operátory porovnávání

Operátory porovnání jsou definovány pro následující typy: `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time` , `DateTimeOffset`. Propagace typu implicitní dochází operandy před použitím relační operátor. Operátory porovnání vždy yield logické hodnoty. Pokud je alespoň jeden z operandy `null`, výsledkem je `null`.

Pro žádný typ objektu, který má identitu, jako jsou definovány rovnosti a nerovnosti `Boolean` typu. Objekty bez primitivní s identitou jsou považovány za shodné, pokud sdílejí stejnou identitu. Následující tabulka uvádí operátory porovnání Entity SQL:

|Operátor|Popis|
|--------------|-----------------|
|[= (Je rovno)](equals-entity-sql.md)|Porovnání rovnosti dvou výrazů.|
|[> (Větší než)](greater-than-entity-sql.md)|Porovná dva výrazy a určit, zda má levý výraz hodnotu větší než pravý výraz.|
|[>= (Větší než nebo rovno)](greater-than-or-equal-to-entity-sql.md)|Porovná dva výrazy a určit, zda má levý výraz hodnotu větší než nebo rovna hodnotě pravý výraz.|
|[JE &AMP;#91;NENÍ&AMP;#93; HODNOTU NULL.](isnull-entity-sql.md)|Určuje, pokud má hodnotu null výrazu dotazu.|
|[< (Méně než)](less-than-entity-sql.md)|Porovná dva výrazy a určit, zda má hodnotu menší, než pravý výraz levý výraz.|
|[<= (Méně než nebo rovno)](less-than-or-equal-to-entity-sql.md)|Porovná dva výrazy a určit, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.|
|[&#91;NOT&#93; BETWEEN](between-entity-sql.md)|Určuje, zda výraz výsledkem hodnota v zadaném rozsahu.|
|[!= (Nerovná se)](not-equal-to-entity-sql.md)|Porovnává dva výrazy k určení, zda není rovno pravý výraz levý výraz.|
|[&#91;NOT&#93; LIKE](like-entity-sql.md)|Určuje, zda řetězec znaků konkrétní odpovídá zadanému vzoru.|

## <a name="logical-and-case-expression-operators"></a>Výraz případu a logické operátory

Logické operátory Testování pravdivosti podmínky. Výraz CASE vyhodnotí sadu logických výrazů k určení výsledku. Následující tabulka uvádí logické a případu výraz operátory:

|Operátor|Popis|
|--------------|-----------------|
|[& & (Logické a)](and-entity-sql.md)|Logickým operátorem a.|
|[! (Logický operátor NOT)](not-entity-sql.md)|Logický operátor NOT.|
|[&#124;&#124;(Nebo logické)](or-entity-sql.md)|Logické OR.|
|[CASE](case-entity-sql.md)|Vyhodnotí sadu logických výrazů k určení výsledku.|
|[THEN](then-entity-sql.md)|Výsledek [při](http://msdn.microsoft.com/library/6233fe9f-00b0-460e-8372-64e138a5f998) klauzule vyhodnocení na hodnotu true.|

## <a name="query-operators"></a>Operátory dotazu

Operátory dotazu se používá k definování výrazy dotazů, které vrací entity data. Následující tabulka uvádí operátory dotazu:

|Operátor|Použití|
|--------------|---------|
|[FROM](from-entity-sql.md)|Určuje kolekci, která se používá v [vyberte](select-entity-sql.md) příkazy.|
|[GROUP BY](group-by-entity-sql.md)|Určuje skupiny, do které objekty, které se vrátí pomocí dotazu ([vyberte](select-entity-sql.md)) výrazu mají být umístěny.|
|[GroupPartition](grouppartition-entity-sql.md)|Vrátí kolekci hodnot argument projektovat vypnout oddílu skupiny, ke kterému se vztahuje na agregaci.|
|[HAVING](having-entity-sql.md)|Určuje podmínku vyhledávání pro skupinu nebo agregace.|
|[LIMIT](limit-entity-sql.md)|Použít s [Order](order-by-entity-sql.md) klauzule, která provádí fyzické stránkování.|
|[ORDER BY](order-by-entity-sql.md)|Určuje, který se používá u objektů, vrátí se v pořadí řazení [vyberte](select-entity-sql.md) příkaz.|
|[SELECT](select-entity-sql.md)|Určuje elementy v projekce, které jsou vrácených dotazem.|
|[SKIP](skip-entity-sql.md)|Použít s [Order](order-by-entity-sql.md) klauzule, která provádí fyzické stránkování.|
|[TOP](top-entity-sql.md)|Určuje, že bude vrácen pouze první sadu řádků z výsledku dotazu.|
|[WHERE](where-entity-sql.md)|Podmíněná filtruje data, která je vrácených dotazem.|

## <a name="reference-operators"></a>Referenční dokumentace operátory

Odkaz je konkrétní entity v sadě konkrétní entitu logické ukazatel (cizí klíč). Entity SQL podporuje následující operátory k vytváření, deconstruct a procházení odkazy:

|Operátor|Použití|
|--------------|---------|
|[CREATEREF](createref-entity-sql.md)|Vytvoří odkazy na entity v sadu entit.|
|[DEREF](deref-entity-sql.md)|Dereferences hodnota odkazu a vytváří výsledek této dereference.|
|[KEY](key-entity-sql.md)|Extrahuje klíč odkaz nebo výraz entity.|
|[NAVIGATE](navigate-entity-sql.md)|Můžete přejít přes vztah z jedna entita typu do jiného|
|[REF](ref-entity-sql.md)|Vrátí odkaz na instanci entity.|

## <a name="set-operators"></a>Operátory set

Entity SQL poskytuje různé operace výkonnou sadu. To zahrnuje operátory set podobná Transact-SQL operátorů, například UNION, INTERSECT, EXCEPT a EXISTS. Operátory Entity SQL také podporuje pro duplicitní odstranění (SET), členství v testování (v) a spojení (připojit). Následující tabulka uvádí operátory set Entity SQL:

|Operátor|Použití|
|--------------|---------|
|[ANYELEMENT](anyelement-entity-sql.md)|Extrahuje element z kolekce s více hodnotami.|
|[EXCEPT](except-entity-sql.md)|Vrátí kolekci všech jedinečných hodnot z výrazu dotazu nalevo od operand EXCEPT nejsou také vrácená z dotazu výrazu napravo od EXCEPT operand.|
|[&#91;NOT&#93; EXISTS](exists-entity-sql.md)|Určuje, zda kolekce je prázdný.|
|[FLATTEN](flatten-entity-sql.md)|Převede kolekci plochou kolekce kolekcí.|
|[&#91;NOT&#93; IN](in-entity-sql.md)|Určuje, zda hodnota odpovídá libovolná hodnota v kolekci.|
|[INTERSECT](intersect-entity-sql.md)|Vrátí kolekci všech jedinečných hodnot, které jsou vráceny ve výrazech dotazů na levé straně a pravé straně operandu INTERSECT.|
|[OVERLAPS](overlaps-entity-sql.md)|Určuje, zda mají dvě kolekce společné prvky.|
|[SET](set-entity-sql.md)|Použít k převedení na kolekci objektů do sady podle je novou kolekci s odebrat všechny duplicitní prvky.|
|[UNION](union-entity-sql.md)|Kombinuje výsledky dvou nebo více dotazů do jedné kolekce.|

## <a name="type-operators"></a>Typ operátory

Entity SQL poskytuje operace, které umožňují typ výrazu (hodnota) sestavený, dotaz a s nimi manipulovat. Následující tabulka uvádí operátory, které se používají k práci s typy:

|Operátor|Použití|
|--------------|---------|
|[CAST](cast-entity-sql.md)|Převod výrazu jednoho datového typu.|
|[COLLECTION](collection-entity-sql.md)|Použít v [funkce](function-entity-sql.md) operaci deklarovat kolekce typy entit a komplexní typy.|
|[JE &AMP;#91;NENÍ&AMP;#93; OF](isof-entity-sql.md)|Určuje, zda typ výrazu je zadaného typu nebo jeden z jeho podtypech.|
|[OFTYPE](oftype-entity-sql.md)|Vrátí kolekci objektů z výrazu dotazu, který je určitého typu.|
|[Konstruktor pojmenovaného typu](named-type-constructor-entity-sql.md)|Použít k vytvoření instance typy entit a komplexní typy.|
|[MULTISET](multiset-entity-sql.md)|Vytvoří instanci multimnožina ze seznamu hodnot.|
|[ROW](row-entity-sql.md)|Vytvoří anonymní, strukturálně typové záznamů z jednoho nebo více hodnot.|
|[TREAT](treat-entity-sql.md)|Objekt konkrétní základní typ zpracovává jako objekt zadaného typu odvozené.|

## <a name="other-operators"></a>Jiné operátory

Následující tabulka uvádí další operátory Entity SQL:

|Operátor|Použití|
|--------------|---------|
|[+ (Zřetězení řetězců)](string-concatenation-entity-sql.md)|Použít ke zřetězení řetězců v Entity SQL.|
|[. (Přístup ke členu)](member-access-entity-sql.md)|Používá pro přístup k hodnotě vlastnost nebo pole instance typu strukturální konceptuálního modelu.|
|[– (komentář)](comment-entity-sql.md)|Zahrnout komentáře Entity SQL.|
|[FUNCTION](function-entity-sql.md)|Definuje vložené funkce, které mohou být provedeny v dotazu Entity SQL.|

## <a name="see-also"></a>Viz také:

[Jazyk Entity SQL](entity-sql-language.md)
