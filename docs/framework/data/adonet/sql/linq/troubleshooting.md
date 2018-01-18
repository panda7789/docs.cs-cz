---
title: "Poradce při potížích"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56d06fa7adf2690a2cb9194342071c7814a4ec4a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="troubleshooting"></a>Poradce při potížích
Následující informace uvádí některé problémy, může dojít ve vaší [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace a poskytuje návrhy k zamezení nebo jinak snížil dopad tyto problémy.  
  
 Další problémy jsou řešeny v [– nejčastější dotazy](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md).  
  
## <a name="unsupported-standard-query-operators"></a>Nepodporované standardní operátory dotazu  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje všechny metody operátor standardní dotazů (například <xref:System.Linq.Enumerable.ElementAt%2A>). Projekty, které kompilovat v důsledku toho může vytvářet stále běhové chyby. Další informace najdete v tématu [operátor překlad dotazu na standardní](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Problémy s pamětí  
 Pokud dotaz zahrnuje kolekci v paměti a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>, dotaz může provést v paměti, v závislosti na pořadí, ve kterém jsou uvedené dvě kolekce. Pokud dotaz musí být spuštěn v paměti, bude nutné data z tabulky databáze mají být načteny.  
  
 Tento přístup je neefektivní a může mít za následek výrazné využití paměti a procesoru. Pokuste se vyhnout takové dotazy víc domén.  
  
## <a name="file-names-and-sqlmetal"></a>Názvy souborů a na SQLMetal  
 Chcete-li zadat název vstupního souboru, přidejte název souboru do příkazového řádku jako vstupní soubor. Včetně názvu souboru v připojovacím řetězci (pomocí **/kontext** možnost) není podporován. Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Projektů knihovny tříd  
 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Vytvoří připojovací řetězec `app.config` souboru projektu. V projektů knihovny tříd `app.config` soubor se nepoužije. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]používá v době návrhu soubory v zadaném připojovacím řetězci. Změna hodnoty v `app.config` nezmění databázi, ke kterému se připojí vaše aplikace.  
  
## <a name="cascade-delete"></a>Kaskádové odstranění  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje nebo rozpoznat kaskádové odstranění operace. Pokud chcete odstranit řádek v tabulce, která má omezení u ní, musíte udělat jednu z těchto věcí:  
  
-   Nastavte `ON DELETE CASCADE` pravidlo v omezení cizího klíče v databázi.  
  
-   Pomocí vlastního kódu nejprve odstranit podřízené objekty, které zabránit odstranění nadřazený objekt.  
  
 V opačném <xref:System.Data.SqlClient.SqlException> je vyvolána výjimka.  
  
 Další informace najdete v tématu [postupy: odstranění řádků z databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
## <a name="expression-not-queryable"></a>Výraz není dotazovatelné  
 Pokud se zobrazí "výraz [výraz] není dotazovatelné; chybějící odkaz na sestavení?" Chyba, zkontrolujte následující:  
  
-   Cílení vaší aplikace [!INCLUDE[compact_v35_short](../../../../../../includes/compact-v35-short-md.md)].  
  
-   Obsahují odkaz na `System.Core.dll` a `System.Data.Linq.dll`.  
  
-   Máte `Imports` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) nebo `using` – direktiva (C#) pro <xref:System.Linq> a <xref:System.Data.Linq>.  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 V průběhu ladění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu, může procházení vztahů entity. Díky tomu přináší tyto položky do mezipaměti, a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se dozví o jejich výskytu. Při spuštění <xref:System.Data.Linq.Table%601.Attach%2A> nebo <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> nebo podobné metoda, která vytváří více řádků, které mají stejný klíč <xref:System.Data.Linq.DuplicateKeyException> je vyvolána výjimka.  
  
## <a name="string-concatenation-exceptions"></a>Řetězec výjimky zřetězení  
 Zřetězení u operandů namapované na `[n]text` a dalších `[n][var]char` není podporován. Pro zřetězení řetězců, které jsou namapované na dvě různé množiny typy je vyvolána výjimka. Další informace najdete v tématu [System.String metody](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>Přeskočit a trvat výjimky v systému SQL Server 2000  
 Je nutné použít identity členy (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) při použití <xref:System.Linq.Queryable.Take%2A> nebo <xref:System.Linq.Queryable.Skip%2A> proti databáze systému SQL Server 2000. Dotaz musí být proti jediné tabulce (tedy ne ke spojení), nebo <xref:System.Linq.Queryable.Distinct%2A>, <xref:System.Linq.Queryable.Except%2A>, <xref:System.Linq.Queryable.Intersect%2A>, nebo <xref:System.Linq.Queryable.Union%2A> operace a nesmí obsahovat <xref:System.Linq.Queryable.Concat%2A> operaci. Další informace najdete v části "Podpora serveru SQL Server 2000" v [operátor překlad dotazu na standardní](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
 Tento požadavek se nevztahuje na [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  
 Tato výjimka se vyvolá, když hodnota sloupce je null v <xref:System.Linq.Enumerable.GroupBy%2A> dotazu, které jsou seskupeny podle `boolean` výrazu, jako například `group x by (Phone==@phone)`. Protože je výraz `boolean`, jako je odvodit klíč `boolean`, nikoli `nullable``boolean`. Při porovnání přeložený vytvoří hodnotu null, je proveden pokus o přiřazení `nullable``boolean` k `boolean`, je vyvolána výjimka.  
  
 Abyste předešli této situaci (za předpokladu, že chcete hodnoty Null považovat za false), použijte přístup například následující:  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>Částečné metody OnCreated()  
 Vygenerovaný metoda `OnCreated()` je volána při každém volání konstruktoru objektu, včetně scénář, ve kterém [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] volá konstruktor k vytvoření kopie pro původní hodnoty. Toto chování vzít v úvahu, pokud budete implementovat `OnCreated()` metoda ve vlastní třídu.  
  
## <a name="see-also"></a>Viz také  
 [Podpora ladění](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 [Nejčastější dotazy](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
