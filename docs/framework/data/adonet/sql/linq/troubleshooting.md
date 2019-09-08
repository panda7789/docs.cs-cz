---
title: Poradce při potížích
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: 0eede70b67cbaef4805fc7fc5f07fc51e342ea3f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780976"
---
# <a name="troubleshooting"></a>Poradce při potížích
Následující informace zpřístupňují některé problémy, se kterými se můžete [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] setkat v aplikacích, a poskytuje návrhy na to, abyste zabránili nebo jinak snížili dopad těchto problémů.  
  
 Další problémy jsou řešeny na [nejčastějších](frequently-asked-questions.md)dotazech.  
  
## <a name="unsupported-standard-query-operators"></a>Nepodporované standardní operátory dotazu  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje všechny standardní metody operátoru dotazu (například <xref:System.Linq.Enumerable.ElementAt%2A>). V důsledku toho projekty, které zkompiluje, mohou stále způsobit chyby za běhu. Další informace naleznete v tématu [standardní převod operátoru dotazu](standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Problémy s pamětí  
 Pokud dotaz zahrnuje kolekci v paměti a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>, může být dotaz spuštěn v paměti v závislosti na pořadí, ve kterém jsou tyto dvě kolekce určeny. Pokud je nutné dotaz provést v paměti, bude nutné načíst data z tabulky databáze.  
  
 Tento přístup je neefektivní a může vést k významnému využití paměti a procesoru. Zkuste se vyhnout takovým dotazům na více doménám.  
  
## <a name="file-names-and-sqlmetal"></a>Názvy souborů a SQLMetal  
 Chcete-li zadat název vstupního souboru, přidejte název souboru do příkazového řádku jako vstupní soubor. Zahrnutí názvu souboru do připojovacího řetězce (pomocí možnosti **/Conn** ) není podporováno. Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Projekty knihovny tříd  
 Návrhář relací objektů vytvoří připojovací řetězec v `app.config` souboru projektu. V projektech `app.config` knihovny tříd se soubor nepoužívá. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]používá připojovací řetězec, který je k dispozici v souborech pro dobu návrhu. Změna hodnoty v `app.config` nemění databázi, ke které se aplikace připojuje.  
  
## <a name="cascade-delete"></a>Kaskádové odstranění  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje ani nerozeznává operace kaskádového odstranění. Pokud chcete odstranit řádek v tabulce, která má omezení proti němu, je nutné provést jednu z následujících akcí:  
  
- `ON DELETE CASCADE` Nastavte pravidlo v omezení cizího klíče v databázi.  
  
- Použijte vlastní kód pro první odstranění podřízených objektů, které brání odstranění nadřazeného objektu.  
  
 V opačném případě je vyvolána výjimka.<xref:System.Data.SqlClient.SqlException>  
  
 Další informace najdete v tématu [jak: Odstraní řádky z databáze](how-to-delete-rows-from-the-database.md).  
  
## <a name="expression-not-queryable"></a>Výraz není Queryable  
 Pokud se zobrazí výraz [výraz] není Queryable; Nechybí odkaz na sestavení? " Chyba, zkontrolujte následující:  
  
- Vaše aplikace cílí na prostředí .NET Compact Framework 3,5.  
  
- Máte odkaz na `System.Core.dll` a `System.Data.Linq.dll`.  
  
- Máte `Imports` direktivu (Visual Basic) nebo `using` (C#) pro <xref:System.Linq> a. <xref:System.Data.Linq>  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 V průběhu ladění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu můžete procházet vztahy entit. Tím se tyto položky přenese do mezipaměti a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ví se o jejich přítomnosti. Pokud se pak pokusíte spustit <xref:System.Data.Linq.Table%601.Attach%2A> nebo <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> podobnou metodu, která vytvoří více řádků se stejným klíčem, <xref:System.Data.Linq.DuplicateKeyException> vyvolá se.  
  
## <a name="string-concatenation-exceptions"></a>Výjimky zřetězení řetězců  
 Zřetězení u operandů mapovaných `[n]text` k a `[n][var]char` jiným není podporováno. Výjimka je vyvolána pro zřetězení řetězců mapovaných na dvě různé sady typů. Další informace naleznete v tématu [metody System. String](system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>Přeskočení a přijetí výjimek v SQL Server 2000  
 Je nutné použít členy identity (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) při použití <xref:System.Linq.Queryable.Take%2A> nebo <xref:System.Linq.Queryable.Skip%2A> k databázi SQL Server 2000. Dotaz musí být na jednu tabulku (to znamená, že není spojení), nebo by se jednat o <xref:System.Linq.Queryable.Distinct%2A>operaci <xref:System.Linq.Queryable.Except%2A>, <xref:System.Linq.Queryable.Intersect%2A>, <xref:System.Linq.Queryable.Concat%2A> nebo <xref:System.Linq.Queryable.Union%2A> a nesmí zahrnovat operaci. Další informace najdete v části Podpora SQL Server 2000 v tématu [standardní převod operátoru dotazu](standard-query-operator-translation.md).  
  
 Tento požadavek neplatí pro SQL Server 2005.  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  
 Tato výjimka je vyvolána, pokud je hodnota sloupce NULL v <xref:System.Linq.Enumerable.GroupBy%2A> dotazu, který seskupuje `boolean` podle výrazu, například `group x by (Phone==@phone)`. Vzhledem k tomu `boolean`, že výraz je, klíč je odvozený `boolean`, nikoli `nullable`. `boolean` Když přeložené porovnání vytvoří hodnotu null, je proveden pokus o přiřazení `nullable` `boolean` k `boolean`a výjimka je vyvolána.  
  
 Chcete-li se této situaci vyhnout (za předpokladu, že chcete považovat hodnoty null za false), použijte následující postup:  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>Částečná metoda s vytvořením ()  
 Vygenerovaná metoda `OnCreated()` je volána pokaždé, když je volán konstruktor objektu, včetně scénáře, ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kterém volá konstruktor, aby vytvořil kopii pro původní hodnoty. Toto chování Vezměte v úvahu, Pokud implementujete `OnCreated()` metodu ve své vlastní dílčí třídě.  
  
## <a name="see-also"></a>Viz také:

- [Podpora ladění](debugging-support.md)
- [Nejčastější dotazy](frequently-asked-questions.md)
