---
title: Identifikátory (entita SQL)
ms.date: 03/30/2017
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
ms.openlocfilehash: 55b9ac101c7849c5b348ba8e48c695c0fa328105
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="identifiers-entity-sql"></a>Identifikátory (entita SQL)
Identifikátory se používají v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] představují aliasy výraz dotazu, odkazy na proměnné, vlastnosti objektů, funkce a tak dále. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nabízí dva typy identifikátorů: jednoduché identifikátory a identifikátory v uvozovkách.  
  
## <a name="simple-identifiers"></a>Jednoduché identifikátory  
 Jednoduchý identifikátor v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je posloupnost alfanumerické znaky a podtržítka. Identifikátor první znak musí být abecedním znakem (a-z nebo A-Z).  
  
## <a name="quoted-identifiers"></a>Identifikátory v uvozovkách  
 Identifikátor uvozovkách je všechny posloupnost znaků uzavřeny do hranatých závorek ([]). Umožňují identifikátory v uvozovkách zadejte identifikátory s znaky, které nejsou platné v identifikátory. Všechny znaky mezi hranaté závorky se stanou součástí identifikátor, včetně všechny prázdné znaky.  
  
 Identifikátor uvozovkách nesmí obsahovat následující znaky:  
  
-   Nový řádek.  
  
-   Návrat na začátek.  
  
-   Karty.  
  
-   BACKSPACE.  
  
-   Další hranaté závorky (tedy hranaté závorky v rámci hranaté závorky, které zobrazit identifikátor).  
  
 V uvozovkách identifikátor může obsahovat znaky znakové sady Unicode.  
  
 Identifikátory v uvozovkách umožňují vytvářet znaků název vlastnosti, které nejsou platné v identifikátory, jak je znázorněno v následujícím příkladu:  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 Identifikátory v uvozovkách můžete taky použít k určení identifikátor, který je vyhrazené klíčové slovo z [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Například pokud typ `Email` má vlastnost s názvem "Od", je můžete odstranit nejednoznačnost ho z rezervované klíčové slovo z pomocí hranaté závorky, následujícím způsobem:  
  
 `SELECT e.[From] FROM emails AS e`  
  
 Na pravé straně operátoru tečku (.) můžete použít identifikátor v uvozovkách.  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 V identifikátoru použít hranatá závorka, přidejte další hranatá závorka. V následujícím příkladu "`abc]`" je identifikátor:  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 Porovnání sémantiku identifikátor v uvozovkách, najdete v části [vstup znaková sada](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="aliasing-rules"></a>Pravidla pro aliasy  
 Doporučujeme, abyste zadání aliasů v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazuje vždy, když je potřeba, včetně následujících [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vytvoří:  
  
-   Pole konstruktoru řádku.  
  
-   Položky v klauzuli FROM výrazu dotazu.  
  
-   Položky v klauzuli SELECT výrazu dotazu.  
  
-   Položky v klauzuli GROUP BY výrazu dotazu.  
  
### <a name="valid-aliases"></a>Platný aliasy  
 Platný aliasy v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou všechny jednoduchý identifikátor nebo identifikátor v uvozovkách.  
  
### <a name="alias-generation"></a>Generování alias  
 Pokud není zadán žádný alias v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz výrazu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí generovat alias na základě následujících pravidel jednoduchý:  
  
-   Pokud ve výrazu dotazu (pro které je alias neurčené) je jednoduchý nebo identifikátor v uvozovkách, tento identifikátor se používá jako alias. Například `ROW(a, [b])` stane `ROW(a AS a, [b] AS [b])`.  
  
-   Pokud ve výrazu dotazu je výraz složitější, ale poslední součástí výrazu tohoto dotazu je jednoduchý identifikátor, tento identifikátor se používá jako alias. Například `ROW(a.a1, b.[b1])` stane `ROW(a.a1 AS a1, b.[b1] AS [b1])`.  
  
 Doporučujeme vám, že nepoužíváte implicitní aliasy Pokud budete chtít později použít název aliasu. Kdykoliv konflikt aliasy (implicitním nebo explicitním) nebo se opakuje ve stejném oboru, bude k chybě kompilace. Implicitní alias předá kompilace, i když je explicitní nebo implicitní alias se stejným názvem.  
  
 Implicitní aliasy jsou vytvořeny automaticky založené na vstup uživatele. Například následující kód vygeneruje název jako alias pro oba sloupce a proto budou v konfliktu.  
  
```  
SELECT product.NAME, person.NAME  
```  
  
 Následující řádek kódu, který používá explicitní aliasy, se také nezdaří. Selhání však bude více zřejmá načtením kód.  
  
```  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a>Pravidla rozsahu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Definuje oboru pravidla, které určují, když konkrétní proměnné jsou viditelné v jazyce dotazu. Některé výrazy nebo příkazy zavést nové názvy. Oboru pravidla určují, kde se dají použít tyto názvy, a pokud nebo kde novou deklaraci se stejným názvem jako jiné můžete skrýt, jeho předchůdce.  
  
 Když se názvy jsou definovány v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu, se nazývá být definován v rámci oboru. Obor obsahuje celou oblast dotazu. Všechny výrazy nebo odkazy na název v rámci určitého oboru můžete zobrazit názvy, které jsou definovány v rámci tohoto oboru. Před zahájením oboru a po jeho ukončení, nelze odkazovat názvy, které jsou definovány v rámci oboru.  
  
 Mohou být vnořené obory. Části [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zavést nové obory, které se týkají celé oblasti, a tyto oblasti může obsahovat jiné [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazů, které také zavádět obory. Když jsou vnořené obory, názvy, které jsou definovány v nejvnitřnější oboru, který obsahuje odkaz na odkazy provádět. Odkazy lze také všechny názvy, které jsou definovány v jakékoli vnější obory. Žádné dva obory, které jsou definované v rámci stejného oboru jsou považovány za obory na stejné úrovni. Není možné provést odkazy na názvy, které jsou definovány v rámci oborů na stejné úrovni.  
  
 Pokud název deklarované v informacích o vnitřní oboru odpovídá názvu deklarovaným ve vnějším oboru, v rámci pro vnitřní obor nebo obory, které jsou deklarované v rámci tohoto oboru o odkazy jenom na nově deklarovaný název. Název v rámci vnějšího oboru je skrytý.  
  
 I v rámci stejného oboru názvů se nemůže odkazovat předtím, než jsou definovány.  
  
 Globální názvy může existovat v rámci prostředí pro spuštění. To může zahrnovat názvy trvalé kolekce nebo proměnné prostředí. Název globální musí být deklarován v nejkrajnější oboru.  
  
 Parametry nejsou v oboru. Protože odkazy na parametry zahrnují speciální syntaxi, názvy parametrů se nikdy dojít ke konfliktu s další názvy v dotazu.  
  
### <a name="query-expressions"></a>Výrazy dotazu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Výraz zavádí nový obor dotazu. Názvy, které jsou definovány v klauzuli FROM vydávají do z oboru v pořadí podle vzhled zleva doprava. V seznamu připojení výrazy mohou odkazovat na názvy, které byly definované výše v seznamu. Veřejné vlastnosti (pole a tak dále) elementů určené v klauzuli FROM nejsou přidány do z oborem. Se musí být vždy odkazuje alias kvalifikovaný název. Obvykle jsou považovány všechny části vyberte výrazu za v rámci z oboru.  
  
 V klauzuli GROUP BY také zavádí nový obor na stejné úrovni. Každá skupina může mít skupina název, který odkazuje na kolekci elementů ve skupině. Každý výraz seskupení také zavádí nový název do oboru skupiny. Agregační vnoření (nebo pojmenovaná skupina) je navíc také přidat do oboru. V rámci z oborem jsou výrazy seskupení sami. Ale pokud je použita klauzule GROUP BY, (projekce) seznamu select, klauzuli HAVING a ORDER BY – klauzule jsou považovány za musí být v oboru skupiny a ne z obor. Agreguje přijímat zvláštní zacházení, jak je popsáno v následujícím seznamu s odrážkami.  
  
 Zde jsou další poznámky o oborech:  
  
-   Seznamu vyberte lze do oboru, postupně zavádět nové názvy. Projekce výrazy vpravo může odkazovat na názvy projekci na levé straně.  
  
-   Klauzuli ORDER by mohou odkazovat na názvy (aliasy) zadané v seznamu select.  
  
-   Pořadí vyhodnocování v rámci vyberte výrazu klauzule určuje pořadí, že jsou názvy vložena do oboru. Klauzule FROM se vyhodnocují jako první, následuje klauzule WHERE, klauzule GROUP BY, klauzule HAVING, klauzuli SELECT a nakonec v klauzuli ORDER BY.  
  
### <a name="aggregate-handling"></a>Souhrnné zpracování  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje dvě formy agregace: na základě kolekce agregované a na základě skupiny položky. Na základě kolekce agregace jsou upřednostňované konstrukce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)], a na základě skupiny agregace jsou podporovány pro SQL kompatibility.  
  
 Při rozpoznávání agregace, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poprvé pokusí o považovat za agregace se na základě kolekce. Pokud to nepomůže, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] transformuje agregační vstup na odkaz k agregaci vnoření a pokusí přeložit nové výrazu, jak je znázorněno v následujícím příkladu.  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Vstupní znaková sada](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)
