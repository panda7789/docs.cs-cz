---
title: Poradce při potížích
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: 697432dce5f7698a8b4eabde3586bb4f77fd62de
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742747"
---
# <a name="troubleshooting"></a>Poradce při potížích
Následující informace uvádí některé problémy, může dojít v vaše [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikací a nabízí návrhy k zamezení nebo jinak snižují dopad těchto problémů.  
  
 Další problémy jsou řešeny v [– nejčastější dotazy](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md).  
  
## <a name="unsupported-standard-query-operators"></a>Nepodporovaná standardních operátorů dotazu  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje všechny standardní metody operátoru dotazu (například <xref:System.Linq.Enumerable.ElementAt%2A>). V důsledku toho projekty, které se kompilují stále způsobit chyby za běhu. Další informace najdete v tématu [standardní překladu – operátor dotazu](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Problémy s pamětí  
 Pokud se dotaz týká kolekci v paměti a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>, mohou být prováděny dotaz v paměti, v závislosti na pořadí, ve kterém jsou uvedeny dvě kolekce. Pokud dotaz musí být spuštěn v paměti, data z tabulky databáze bude muset načíst.  
  
 Tento přístup je neefektivní a může mít za následek výrazné využití paměti a procesoru. Snažte se vyhnout takové dotazy víc domén.  
  
## <a name="file-names-and-sqlmetal"></a>Názvy souborů a SQLMetal  
 Chcete-li zadat název vstupního souboru, přidejte název souboru do příkazového řádku jako vstupní soubor. Včetně názvu souboru do připojovacího řetězce (pomocí **/conn** možnost) se nepodporuje. Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Projekty knihovny tříd  
 Návrhář relací objektů vytvoří připojovací řetězec v `app.config` souboru projektu. V projektech knihoven tříd `app.config` soubor nepoužívá. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používá připojovací řetězec k dispozici v souborech návrhu. Změna hodnoty v `app.config` nezmění databázi, do kterého vaše aplikace připojuje.  
  
## <a name="cascade-delete"></a>Kaskádové odstranění  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje ani rozpoznat kaskádové odstranění operace. Pokud chcete odstranit řádek v tabulce, která má omezení u ní, musíte udělat jednu z následujících akcí:  
  
- Nastavte `ON DELETE CASCADE` pravidlo v omezení cizího klíče v databázi.  
  
- Pomocí vlastního kódu nejprve odstranit podřízené objekty, které brání nadřazený objekt odstranit.  
  
 V opačném případě <xref:System.Data.SqlClient.SqlException> je vyvolána výjimka.  
  
 Další informace najdete v tématu [jak: Odstranit řádky z databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
## <a name="expression-not-queryable"></a>Výraz není dotazovatelné  
 Pokud se zobrazí "výraz [výrazu] není dotazovatelné; chybí vám odkaz na sestavení?" Chyba, ujistěte se, že z následujících akcí:  
  
- Vaše aplikace cílí na rozhraní .NET Compact Framework 3.5.  
  
- Budete mít odkaz na `System.Core.dll` a `System.Data.Linq.dll`.  
  
- Máte `Imports` (Visual Basic) nebo `using` – direktiva (C#) pro <xref:System.Linq> a <xref:System.Data.Linq>.  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 Při ladění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu, může procházet vztahy entity. To přináší tyto položky do mezipaměti, a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se dozví o jejich výskytu. Pokud se potom pokusíte o provedení <xref:System.Data.Linq.Table%601.Attach%2A> nebo <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> nebo podobné metody, která vytváří více řádků, které mají stejný klíč <xref:System.Data.Linq.DuplicateKeyException> je vyvolána výjimka.  
  
## <a name="string-concatenation-exceptions"></a>Řetězec výjimky zřetězení  
 Zřetězení na operandech namapované na `[n]text` a dalších `[n][var]char` se nepodporuje. Pro zřetězení řetězců, které jsou namapovány na dvě různé sady typů je vyvolána výjimka. Další informace najdete v tématu [metody System.String](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>Přeskočit a převzít výjimky v systému SQL Server 2000  
 Je nutné použít identity členy (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) při použití <xref:System.Linq.Queryable.Take%2A> nebo <xref:System.Linq.Queryable.Skip%2A> databázi systému SQL Server 2000. Dotaz musí být před jedné tabulky (to znamená, nikoli spojení) nebo <xref:System.Linq.Queryable.Distinct%2A>, <xref:System.Linq.Queryable.Except%2A>, <xref:System.Linq.Queryable.Intersect%2A>, nebo <xref:System.Linq.Queryable.Union%2A> operace a nesmějí obsahovat <xref:System.Linq.Queryable.Concat%2A> operace. Další informace najdete v části "Podpora serveru SQL Server 2000" v [standardní překladu – operátor dotazu](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
 Tento požadavek se nevztahuje na systém SQL Server 2005.  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  
 Tato výjimka se vyvolá, když má hodnotu null ve sloupci Hodnota <xref:System.Linq.Enumerable.GroupBy%2A> dotaz, který se seskupí podle `boolean` výraz, například `group x by (Phone==@phone)`. Protože je výraz `boolean`, klíč odvozena jako `boolean`, nikoli `nullable` `boolean`. Pokud přeloženou porovnání vytvoří s hodnotou null, je proveden pokus o přiřazení `nullable` `boolean` k `boolean`, a je vyvolána výjimka.  
  
 Abyste předešli této situaci (za předpokladu, že chcete zpracovávat hodnoty null jako hodnotu false), použijte přístup například následující:  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>Částečná metoda OnCreated()  
 Vytvořena metoda `OnCreated()` je volána pokaždé, když je volána konstruktor objektu, včetně scénář, ve kterém [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] volá konstruktor k vytvoření kopie pro původní hodnoty. Toto chování vzít v úvahu, pokud se rozhodnete implementovat `OnCreated()` metoda ve vlastním částečné třídy.  
  
## <a name="see-also"></a>Viz také:

- [Podpora ladění](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
- [Nejčastější dotazy](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
