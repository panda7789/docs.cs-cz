---
title: Identifikátory (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
ms.openlocfilehash: 390c69dec6caed1ffe6faccb5893174d2c211a6b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528577"
---
# <a name="identifiers-entity-sql"></a>Identifikátory (Entity SQL)
Identifikátory se používají v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] představující aliasy výraz dotazu, odkazy na proměnné, vlastnosti objektů, funkcí a tak dále. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje dva typy identifikátorů: jednoduché identifikátory a identifikátory v uvozovkách.  
  
## <a name="simple-identifiers"></a>Jednoduché identifikátory  
 Jednoduchý identifikátor. v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je posloupnost alfanumerické znaky a znaky podtržení. První znak identifikátoru musí být abecední znak (a-z nebo A-Z).  
  
## <a name="quoted-identifiers"></a>Identifikátory v uvozovkách  
 Identifikátor v uvozovkách je libovolnou posloupností znaků uzavřeny do hranatých závorek ([]). Umožňuje identifikátory v uvozovkách zadejte znaky, které nejsou platné v identifikátorech identifikátory. Všechny znaky mezi hranaté závorky se stanou součástí identifikátoru, včetně všech mezer.  
  
 Identifikátor v uvozovkách nesmí obsahovat následující znaky:  
  
-   Nový řádek.  
  
-   Návrat.  
  
-   Karty.  
  
-   BACKSPACE.  
  
-   Další hranaté závorky (to znamená, hranaté závorky v hranatých závorkách, která od sebe odděluje identifikátor).  
  
 V uvozovkách identifikátor může obsahovat znaky Unicode.  
  
 Identifikátory v uvozovkách umožňují vytvářet znaky názvu vlastnosti, které nejsou platné v identifikátorech, jak je znázorněno v následujícím příkladu:  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 Identifikátory v uvozovkách můžete také použít k určení identifikátor, který je vyhrazené klíčové slovo z [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Například pokud typ `Email` má vlastnost s názvem "Z", je můžete odstranit nejednoznačnost ho z vyhrazené klíčové slovo z pomocí hranatých závorek:  
  
 `SELECT e.[From] FROM emails AS e`  
  
 Na pravé straně operátoru tečka (.) můžete použít identifikátor v uvozovkách.  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 Chcete-li v identifikátoru použít hranatá závorka, přidejte další hranatá závorka. V následujícím příkladu "`abc]`" je identifikátor:  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 Sémantika porovnání identifikátor v uvozovkách, naleznete v tématu [vstupní znaková sada](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="aliasing-rules"></a>Pravidla pro aliasy  
 Doporučujeme, abyste zadání aliasů v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazuje pokaždé, když je nepotřebujete, včetně následujících [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vytvoří:  
  
-   Pole konstruktoru řádku.  
  
-   Položky v klauzuli FROM výrazu dotazu.  
  
-   Položky v klauzuli SELECT výrazu dotazu.  
  
-   Položky v klauzuli GROUP BY výrazu dotazu.  
  
### <a name="valid-aliases"></a>Platný aliasy  
 Platný aliasů v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou nějaké jednoduchý identifikátor nebo identifikátor v uvozovkách.  
  
### <a name="alias-generation"></a>Generování alias  
 Pokud není zadán žádný alias v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazu, dotazu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vygenerovat alias na základě následujících pravidel jednoduchý:  
  
-   Pokud výraz dotazu (pro který je alias neurčené) je jednoduchý nebo identifikátor v uvozovkách, tento identifikátor se používá jako alias. Například `ROW(a, [b])` stane `ROW(a AS a, [b] AS [b])`.  
  
-   Pokud výraz dotazu je složitější výraz, ale poslední součástí tohoto výrazu dotazu je jednoduchý identifikátor, tento identifikátor se používá jako alias. Například `ROW(a.a1, b.[b1])` stane `ROW(a.a1 AS a1, b.[b1] AS [b1])`.  
  
 Doporučujeme, abyste je velmi riskantní používat implicitní aliasing. Pokud budete chtít později použít název aliasu. Kdykoli konfliktů aliasů (implicitní nebo explicitní) nebo jsou opakovaný ve stejném oboru, bude existovat chyby kompilace. Implicitní alias předá kompilace i v případě, že se explicitní nebo implicitní alias se stejným názvem.  
  
 Implicitní aliasy jsou automaticky generované na základě uživatelského zadání. Například následující řádek kódu bude generovat název jako alias pro oba sloupce a proto budou v konfliktu.  
  
```  
SELECT product.NAME, person.NAME  
```  
  
 Následující řádek kódu, který používá explicitní aliasy, se také nezdaří. Ale selhání bude více pozná se čtením kódu.  
  
```  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a>Pravidla vytváření oborů  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Definuje pravidel stanovení rozsahu, které určují, když konkrétní proměnné jsou viditelné v dotazovacím jazyce. Některé výrazy nebo příkazy zavádí nové názvy. Oboru pravidla určují, kde je možné tyto názvy a kdy a kde novou deklaraci se stejným názvem jako jiný lze skrýt jeho předchůdce.  
  
 Když se názvy jsou definovány v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu, se říká, že je definovat v rámci oboru. Obor pokrývá celou oblast dotazu. Všechny výrazy nebo odkazy na název v rámci určitého oboru můžete zobrazit názvy, které jsou definovány v daném oboru. Před zahájením oboru a po jeho skončení, názvy, které jsou definovány v rámci oboru nelze odkazovat.  
  
 Mohou být vnořené obory. Části [!INCLUDE[esql](../../../../../../includes/esql-md.md)] představují nové obory, které pokrývají celou oblastech, a tyto oblasti mohou obsahovat jiné [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazy, které přinášejí s sebou obory. Když jsou vnořené obory, názvy, které jsou definovány v nejvnitřnější obor, který obsahuje odkaz na odkazy provádět. Odkazy taky provádět žádné názvy, které jsou definovány v jakékoli vnější obory. Žádné dva obory definované v rámci stejného oboru, jsou považovány za obory na stejné úrovni. Odkazy nelze nastavit na názvy, které jsou definovány v rámci oborů na stejné úrovni.  
  
 Pokud je název deklarovaný ve vnitřním oboru odpovídá názvu deklarována ve vnějším oboru, vnitřní obor nebo v rámci oborů deklarované v rámci tohoto oboru odkazy pouze na název nově deklarovaný. Je skrytý názvu ve vnějším oboru.  
  
 Dokonce i v rámci stejného oboru názvů se nedá odkazovat předtím, než jsou definovány.  
  
 Globální názvy může existovat jako součást spouštěcího prostředí. To může zahrnovat názvy kolekcí trvalé nebo proměnné prostředí. Název globální musí být deklarována ve vnějším oboru.  
  
 Parametry nejsou v oboru. Protože odkazy na parametry zahrnují speciální syntaxi, názvy parametrů se nikdy kolidují s názvy jiných v dotazu.  
  
### <a name="query-expressions"></a>Výrazy dotazu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zavádí nový obor výrazu dotazu. Názvy, které jsou definovány v klauzuli FROM umístěni do z oboru v pořadí vzhled, zleva doprava. V seznamu spojení výrazy mohou odkazovat na názvy, které byly dříve definovány v seznamu. Veřejné vlastnosti (pole a tak dále) prvků identifikované v klauzuli FROM nejsou přidány do z rozsahu. Musí být vždy odkazuje alias kvalifikovaný název. Obvykle jsou považovány všechny části vyberte výrazu za v rámci z oboru.  
  
 V klauzuli GROUP BY také zavádí nový obor na stejné úrovni. Každá skupina může mít skupina název, který odkazuje na kolekci prvků ve skupině. Každý výraz grouping také zavádí nový název do oboru skupiny. Vnoření agregace (nebo pojmenované skupiny) je navíc také přidat do oboru. Výrazy seskupení sami jsou v rámci z oboru. Ale při použití klauzule GROUP BY (projekce) seznamu select, klauzuli HAVING a ORDER BY – klauzule jsou považovány za v rámci oboru skupiny a ne z oboru. Agregace přijímat zvláštní zacházení, jak je popsáno v následujícím seznamu s odrážkami.  
  
 Tady jsou další poznámky o oborech:  
  
-   Seznamu select můžou představovat nové názvy na obor, v pořadí. Projekce výrazy na pravé straně může odkazovat na názvy plánovaných na levé straně.  
  
-   Klauzule ORDER by mohou odkazovat na názvy (aliasy) zadané v seznamu select.  
  
-   Pořadí vyhodnocování klauzule v rámci vyberte výraz určuje pořadí, že jsou názvy zařadit do oboru. Klauzule FROM vyčíslen první, za nímž následuje klauzule WHERE, GROUP BY – klauzule, klauzuli HAVING, klauzule SELECT a nakonec klauzule ORDER by.  
  
### <a name="aggregate-handling"></a>Agregovat zpracování  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje dvě formy agregace: na základě kolekce agregace a agregace podle skupin. Na základě kolekce agregace jsou upřednostňované konstrukce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)], a na základě skupin agregace jsou podporovány pro kompatibilitu SQL.  
  
 Při překladu agregace, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nejdříve pokusí ji považovat za agregaci na základě kolekce. Pokud se to nepodaří, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] transformuje agregační vstup do odkazu vnoření agregaci a pokusí přeložit nový výrazu, jak je znázorněno v následujícím příkladu.  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Vstupní znaková sada](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)
