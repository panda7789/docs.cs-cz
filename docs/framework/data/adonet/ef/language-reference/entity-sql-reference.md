---
title: Odkaz na entitu SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 776a2a93f559ba54651adc49e6b609c8156e9e31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="entity-sql-reference"></a>Odkaz na entitu SQL
Tato část obsahuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] referenční témata. Toto téma shrnuje a skupin [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory podle kategorie.  
  
## <a name="arithmetic-operators"></a>Aritmetické operátory  
 Aritmetické operátory provádět matematické operace dvou výrazů jeden nebo více číselné datové typy. Následující tabulka uvádí [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aritmetické operátory.  
  
|Operátor|Použití|  
|--------------|---------|  
|[+ (Přidat)](../../../../../../docs/framework/data/adonet/ef/language-reference/add.md)|Přidání.|  
|"/ (Dělení)"|Dělení.|  
|[% (Modulo)](../../../../../../docs/framework/data/adonet/ef/language-reference/modulo-entity-sql.md)|Vrátí zbytek dělení.|  
|[* (Násobení)](../../../../../../docs/framework/data/adonet/ef/language-reference/multiply-entity-sql.md)|Násobení.|  
|[-(Záporné hodnoty)](../../../../../../docs/framework/data/adonet/ef/language-reference/negative-entity-sql.md)|Negace.|  
|[-(Odečtena)](../../../../../../docs/framework/data/adonet/ef/language-reference/subtract-entity-sql.md)|Odčítání.|  
  
## <a name="canonical-functions"></a>Kanonické funkce  
 Kanonické funkce jsou podporovány všechny zprostředkovateli dat a mohou být využívána všechny dotazování technologie. Následující tabulka uvádí kanonické funkce.  
  
|Funkce|Typ|  
|--------------|----------|  
|[Funkce kanonické agregační Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|Popisuje agregace [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.|  
|[Matematické funkce kanonickém tvaru](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|Popisuje matematické [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.|  
|[Kanonické funkce řetězce](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|Popisuje řetězec [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.|  
|[Kanonické funkce data a času](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|Popisuje data a času [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.|  
|[Bitový kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|Popisuje bitový [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.|  
|[Další kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)|Popisuje funkce není klasifikovaný bitové, datum a čas, řetězec, matematické nebo agregace.|  
  
## <a name="comparison-operators"></a>Operátory porovnání  
 Operátory porovnání jsou definovány pro následující typy: `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time` , `DateTimeOffset`. Propagace typu implicitní dochází operandy před použitím relační operátor. Operátory porovnání vždy yield logické hodnoty. Pokud je alespoň jeden z operandy `null`, výsledkem je `null`.  
  
 Pro žádný typ objektu, který má identitu, jako jsou definovány rovnosti a nerovnosti `Boolean` typu. Objekty bez primitivní s identitou jsou považovány za shodné, pokud sdílejí stejnou identitu. Následující tabulka uvádí [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory porovnání.  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[= (Je rovno)](../../../../../../docs/framework/data/adonet/ef/language-reference/equals-entity-sql.md)|Porovnání rovnosti dvou výrazů.|  
|[> (Větší než)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-entity-sql.md)|Porovná dva výrazy a určit, zda má levý výraz hodnotu větší než pravý výraz.|  
|[> = (větší než nebo rovno)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-or-equal-to-entity-sql.md)|Porovná dva výrazy a určit, zda má levý výraz hodnotu větší než nebo rovna hodnotě pravý výraz.|  
|[JE &#91; NE &#93; HODNOTU NULL](../../../../../../docs/framework/data/adonet/ef/language-reference/isnull-entity-sql.md)|Určuje, pokud má hodnotu null výrazu dotazu.|  
|[< (Méně než)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-entity-sql.md)|Porovná dva výrazy a určit, zda má hodnotu menší, než pravý výraz levý výraz.|  
|[< = (je menší než nebo rovno)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-or-equal-to-entity-sql.md)|Porovná dva výrazy a určit, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.|  
|[&#91; NE &#93; MEZI](../../../../../../docs/framework/data/adonet/ef/language-reference/between-entity-sql.md)|Určuje, zda výraz výsledkem hodnota v zadaném rozsahu.|  
|[! = (Nerovná se)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-equal-to-entity-sql.md)|Porovnává dva výrazy k určení, zda levý výraz není rovno pravý výraz.|  
|[&#91; NE &#93; JAKO](../../../../../../docs/framework/data/adonet/ef/language-reference/like-entity-sql.md)|Určuje, zda řetězec znaků konkrétní odpovídá zadanému vzoru.|  
  
## <a name="logical-and-case-expression-operators"></a>Výraz případu a logické operátory  
 Logické operátory Testování pravdivosti podmínky. Výraz CASE vyhodnotí sadu logických výrazů k určení výsledku. Následující tabulka uvádí logické a případu výraz operátory.  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[& & (Logické a)](../../../../../../docs/framework/data/adonet/ef/language-reference/and-entity-sql.md)|Logickým operátorem a.|  
|[! (Logický operátor NOT)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-entity-sql.md)|Logický operátor NOT.|  
|[&#124; &#124; (Nebo logické)](../../../../../../docs/framework/data/adonet/ef/language-reference/or-entity-sql.md)|Logické OR.|  
|[PŘÍPAD](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)|Vyhodnotí sadu logických výrazů k určení výsledku.|  
|[POTOM](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)|Výsledek [při](http://msdn.microsoft.com/en-us/6233fe9f-00b0-460e-8372-64e138a5f998) klauzule vyhodnocení na hodnotu true.|  
  
## <a name="query-operators"></a>Operátory dotazů  
 Operátory dotazu se používá k definování výrazy dotazů, které vrací entity data. Následující tabulka uvádí operátory dotazu.  
  
|Operátor|Použití|  
|--------------|---------|  
|[Z](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)|Určuje kolekci, která se používá v [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) příkazy.|  
|[SESKUPIT PODLE](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)|Určuje skupiny, do které objekty, které se vrátí pomocí dotazu ([vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) výrazu mají být umístěny.|  
|[GroupPartition](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md)|Vrátí kolekci hodnot argument projektovat vypnout oddílu skupiny, ke kterému se vztahuje na agregaci.|  
|[S](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)|Určuje podmínku vyhledávání pro skupinu nebo agregace.|  
|[LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)|Použít s [Order](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzule, která provádí fyzické stránkování.|  
|[ŘADIT PODLE](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)|Určuje, který se používá u objektů, vrátí se v pořadí řazení [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) příkaz.|  
|[VYBERTE](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)|Určuje elementy v projekce, které jsou vrácených dotazem.|  
|[PŘESKOČIT](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)|Použít s [Order](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzule, která provádí fyzické stránkování.|  
|[HORNÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)|Určuje, že bude vrácen pouze první sadu řádků z výsledku dotazu.|  
|[KDE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)|Podmíněná filtruje data, která je vrácených dotazem.|  
  
## <a name="reference-operators"></a>Referenční dokumentace operátory  
 Odkaz je konkrétní entity v sadě konkrétní entitu logické ukazatel (cizí klíč). [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje následující operátory k vytváření, deconstruct a procházení odkazy.  
  
|Operátor|Použití|  
|--------------|---------|  
|[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)|Vytvoří odkazy na entity v sadu entit.|  
|[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)|Dereferences hodnota odkazu a vytváří výsledek této dereference.|  
|[KLÍČ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)|Extrahuje klíč odkaz nebo výraz entity.|  
|[PŘEJDĚTE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)|Můžete přejít přes vztah z jedna entita typu do jiného|  
|[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)|Vrátí odkaz na instanci entity.|  
  
## <a name="set-operators"></a>Operátory set  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje různé operace výkonnou sadu. To zahrnuje operátory set podobná Transact-SQL operátorů, například UNION, INTERSECT, EXCEPT a EXISTS. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]také podporuje operátory pro odstranění duplicit (SET), členství v testování (v) a spojení (připojit). Následující tabulka uvádí [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.  
  
|Operátor|Použití|  
|--------------|---------|  
|[ANYELEMENT](../../../../../../docs/framework/data/adonet/ef/language-reference/anyelement-entity-sql.md)|Extrahuje element z kolekce s více hodnotami.|  
|[S VÝJIMKOU](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)|Vrátí kolekci všech jedinečných hodnot z výrazu dotazu nalevo od operand EXCEPT nejsou také vrácená z dotazu výrazu napravo od EXCEPT operand.|  
|[&#91; NE &#93; EXISTUJE](../../../../../../docs/framework/data/adonet/ef/language-reference/exists-entity-sql.md)|Určuje, zda kolekce je prázdný.|  
|[VYROVNÁNÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/flatten-entity-sql.md)|Převede kolekci plochou kolekce kolekcí.|  
|[&#91; NE &#93; V](../../../../../../docs/framework/data/adonet/ef/language-reference/in-entity-sql.md)|Určuje, zda hodnota odpovídá libovolná hodnota v kolekci.|  
|[INTERSECT](../../../../../../docs/framework/data/adonet/ef/language-reference/intersect-entity-sql.md)|Vrátí kolekci všech jedinečných hodnot, které jsou vráceny ve výrazech dotazů na levé straně a pravé straně operandu INTERSECT.|  
|[PŘEKRYTÍ.](../../../../../../docs/framework/data/adonet/ef/language-reference/overlaps-entity-sql.md)|Určuje, zda mají dvě kolekce společné prvky.|  
|[NASTAVENÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/set-entity-sql.md)|Použít k převedení na kolekci objektů do sady podle je novou kolekci s odebrat všechny duplicitní prvky.|  
|[SJEDNOCENÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/union-entity-sql.md)|Kombinuje výsledky dvou nebo více dotazů do jedné kolekce.|  
  
## <a name="type-operators"></a>Typ operátory  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje operace, které umožňují typ výrazu (hodnota) sestavený, dotaz a s nimi manipulovat. Následující tabulka uvádí operátory, které se používají k práci s typy.  
  
|Operátor|Použití|  
|--------------|---------|  
|[PŘETYPOVÁNÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)|Převod výrazu jednoho datového typu.|  
|[KOLEKCE](../../../../../../docs/framework/data/adonet/ef/language-reference/collection-entity-sql.md)|Použít v [funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operaci deklarovat kolekce typy entit a komplexní typy.|  
|[JE &#91; NE &#93; Z](../../../../../../docs/framework/data/adonet/ef/language-reference/isof-entity-sql.md)|Určuje, zda typ výrazu je zadaného typu nebo jeden z jeho podtypech.|  
|[OFTYPE](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)|Vrátí kolekci objektů z výrazu dotazu, který je určitého typu.|  
|[Konstruktor typu s názvem](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)|Použít k vytvoření instance typy entit a komplexní typy.|  
|[MULTIMNOŽINA](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)|Vytvoří instanci multimnožina ze seznamu hodnot.|  
|[ŘÁDEK](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)|Vytvoří anonymní, strukturálně typové záznamů z jednoho nebo více hodnot.|  
|[ZPRACOVÁVAT](../../../../../../docs/framework/data/adonet/ef/language-reference/treat-entity-sql.md)|Objekt konkrétní základní typ zpracovává jako objekt zadaného typu odvozené.|  
  
## <a name="other-operators"></a>Jiné operátory  
 Následující tabulka uvádí další [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory.  
  
|Operátor|Použití|  
|--------------|---------|  
|[+ (Zřetězení)](../../../../../../docs/framework/data/adonet/ef/language-reference/string-concatenation-entity-sql.md)|Použít ke zřetězení řetězců v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[. (Přístup ke členu)](../../../../../../docs/framework/data/adonet/ef/language-reference/member-access-entity-sql.md)|Používá pro přístup k hodnotě vlastnost nebo pole instance typu strukturální konceptuálního modelu.|  
|[--(Komentář)](../../../../../../docs/framework/data/adonet/ef/language-reference/comment-entity-sql.md)|Zahrnout [!INCLUDE[esql](../../../../../../includes/esql-md.md)] komentáře.|  
|[FUNKCE](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)|Definuje vložené funkce, které mohou být provedeny v dotazu Entity SQL.|  
  
## <a name="see-also"></a>Viz také  
 [Jazyk SQL entity](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
