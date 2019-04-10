---
title: Nejčastější dotazy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 20c5ee3667bf57328a3b6dda6e55dce4ddbbec72
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223976"
---
# <a name="frequently-asked-questions"></a>Nejčastější dotazy
V dalších částech odpovědět některé běžné problémy, které se mohou vyskytnout při implementaci [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 Další problémy jsou řešeny v [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="cannot-connect"></a>Nejde se připojit  
 Otázka: Nejde se připojit k databázi.  
  
 A. Ujistěte se, že je připojovací řetězec správný a že je spuštěna instance serveru SQL Server. Všimněte si také, že [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vyžaduje, aby byl povolen protokol pojmenovaných kanálů. Další informace najdete v tématu [učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
## <a name="changes-to-database-lost"></a>Změny v databázi ztráty  
 Otázka: Provedené změny dat v databázi, ale když mám reran Moje aplikace, změny byl již existuje.  
  
 A. Ujistěte se, že zavoláte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> uložte výsledky do databáze.  
  
## <a name="database-connection-open-how-long"></a>Připojení k databázi: Jak dlouho otevřít?  
 Otázka: Jak dlouho připojení k databázi zůstaly otevřené?  
  
 A. Připojení obvykle zůstane otevřený, dokud využívání výsledky dotazu. Pokud očekáváte, že se čas ke zpracování výsledků a jsou není rozdíl od ukládání do mezipaměti výsledky, použijte <xref:System.Linq.Enumerable.ToList%2A> v dotazu. V běžných situacích, kdy každý objekt se zpracovává jenom jednou, model streamování jedničkou v obou `DataReader` a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Podrobnosti o použití připojení závisí na následujících akcí:  
  
-   Stav připojení Pokud <xref:System.Data.Linq.DataContext> je vytvořený pomocí objekt připojení.  
  
-   Nastavení připojovacího řetězce (například povolení více aktivních sad výsledků (MARS). Další informace najdete v tématu [více sad aktivní výsledků (MARS)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md).  
  
## <a name="updating-without-querying"></a>Aktualizuje se bez dotazování  
 Otázka: Můžete aktualizovat data v tabulce bez první dotazování na databázi?  
  
 A. I když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemá žádné příkazy na základě sady aktualizace aktualizovat bez nutnosti první dotazování můžete použít některou z následujících postupů:  
  
-   Použití <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> poslat kód SQL.  
  
-   Vytvoření nové instance objektu a inicializovat všechny aktuální hodnoty (pole), které mají vliv aktualizace. Připojte objekt, který má <xref:System.Data.Linq.DataContext> pomocí <xref:System.Data.Linq.Table%601.Attach%2A> a upravit pole, které chcete změnit.  
  
## <a name="unexpected-query-results"></a>Neočekávaný dotaz výsledky  
 Otázka: Můj dotaz vrací neočekávané výsledky. Jak lze můžu zkontrolovat, co se děje?  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje několik nástrojů pro zkontrolujete kód SQL, který generuje. Jednou z vašich nejdůležitějších je <xref:System.Data.Linq.DataContext.Log%2A>. Další informace najdete v tématu [podporu ladění](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="unexpected-stored-procedure-results"></a>Uložená procedura neočekávané výsledky  
 Otázka: Mám uložené procedury, vrácená hodnota je vypočítána `MAX()`. Při přetahování uložené procedury, která [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] surface, vrácená hodnota není správný.  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] návratové hodnoty generovaných databází pomocí uložených procedur dvěma způsoby:  
  
-   Pojmenováním výsledných výstupů.  
  
-   Explicitním zadáním výstupní parametr.  
  
 Následuje příklad výstupu nesprávné. Protože [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nelze mapovat výsledky, vždy vrátí hodnotu 0:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select max(i) from t where name like 'hello'`  
  
 `end`  
  
 Následující je příklad výstupu správné pomocí výstupní parametr:  
  
 `create procedure proc2`  
  
 `@result int OUTPUT`  
  
 `as`  
  
 `select @result = MAX(i) from t where name like 'hello'`  
  
 `go`  
  
 Následující je příklad výstupu správné pojmenováním výstup výsledku:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select nax(i) AS MaxResult from t where name like 'hello'`  
  
 `end`  
  
 Další informace najdete v tématu [přizpůsobení operací pomocí pomocí uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md).  
  
## <a name="serialization-errors"></a>Chyby serializace  
 Otázka: Při serializaci, zobrazí následující chybová zpráva: "Zadejte... 'System.Data.Linq.ChangeTracker+StandardChangeTracker' není označen jako serializovatelný."  
  
 A. Generování v kódu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje <xref:System.Runtime.Serialization.DataContractSerializer> serializace. Nepodporuje <xref:System.Xml.Serialization.XmlSerializer> nebo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Další informace najdete v tématu [serializace](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md).  
  
## <a name="multiple-dbml-files"></a>Více soubory DBML  
 Otázka: Pokud mám více DBML soubory, které sdílejí společné některé tabulky, obdržím chybu kompilátoru.  
  
 A. Nastavte **kontextu Namespace** a **Entity Namespace** vlastnosti z [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] na hodnotu odlišné pro každého souboru DBML. Tento přístup se eliminují kolizí název nebo obor názvů.  
  
## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>Jak se vyhnout explicitní nastavení hodnot generovaných databází na Insert nebo Update  
 Otázka: Budu mít databázové tabulce `DateCreated` sloupec, který se výchozí hodnota je SQL `Getdate()`. Při pokusu vložit nový záznam s použitím [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], získá hodnotu `NULL`. Byste očekávali ji nastavit na výchozí databáze  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zpracovává tuto situaci automaticky pro identitu (automatické zvyšování čísla) a rowguidcol (GUID databáze vygenerovala) a sloupce časového razítka. V ostatních případech byste měli ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> = `true` a <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> vlastnosti.  
  
## <a name="multiple-dataloadoptions"></a>Více DataLoadOptions  
 Otázka: Můžete zadat další zátěž možnosti bez přepsání první?  
  
 A. Ano. První není přepsán, jako v následujícím příkladu:  
  
```vb  
Dim dlo As New DataLoadOptions()  
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)  
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)  
```  
  
```csharp  
DataLoadOptions dlo = new DataLoadOptions();  
dlo.LoadWith<Order>(o => o.Customer);  
dlo.LoadWith<Order>(o => o.OrderDetails);  
```  
  
## <a name="errors-using-sql-compact-35"></a>Chyby pomocí SQL Compact 3,5  
 Otázka: Při přetahování tabulek z celkového počtu se zobrazí chyba [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] databáze.  
  
 A. [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nepodporuje [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)], i když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] neodpovídá modulu runtime. V takovém případě musíte vytvořit vlastní entity třídy a přidejte příslušné atributy.  
  
## <a name="errors-in-inheritance-relationships"></a>Chyby ve vztazích dědičnosti  
 Otázka: Můžu použít tvar dědičnosti sady nástrojů v [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] připojit dvěma entitami, ale nemůžu dojde k chybám.  
  
 A. Vytvoření relace není dostatečně. Je třeba zadat informace, jako je například sloupec diskriminátoru, hodnota diskriminátoru základní třídy a odvozené třídy hodnota diskriminátoru.  
  
## <a name="provider-model"></a>Model poskytovatele  
 Otázka: Je k dispozici modelem veřejného poskytovatele?  
  
 A. Je k dispozici žádný model veřejného poskytovatele. V tuto chvíli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje SQL Server a [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] pouze.  
  
## <a name="sql-injection-attacks"></a>Útoky prostřednictvím injektáže SQL  
 Otázka: Jak je [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] chránit před útoky prostřednictvím injektáže SQL?  
  
 A. Útok prostřednictvím injektáže SQL se významné riziko pro tradiční dotazy SQL vytvořený zřetězením vstup uživatele. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zabraňuje takové vkládání pomocí <xref:System.Data.SqlClient.SqlParameter> v dotazech. Uživatelský vstup je převedena na hodnoty parametrů. Tento postup brání použití ze vstupu zákazníka škodlivých příkazů.  
  
## <a name="changing-read-only-flag-in-dbml-files"></a>Změna příznak jen pro čtení v soubory DBML  
 Otázka: Jak se při vytvoření objektového modelu ze souboru DBML eliminovat setter z některých vlastností?  
  
 A. Proveďte následující kroky pro tento scénář rozšířené:  
  
1.  V souboru DBML, upravte vlastnost tak, že změníte <xref:System.Data.Linq.ITable.IsReadOnly%2A> příznak `True`.  
  
2.  Přidejte částečnou třídu. Vytvořte konstruktor s parametry pro členy jen pro čtení.  
  
3.  Zkontrolujte výchozí <xref:System.Data.Linq.Mapping.UpdateCheck> hodnotu (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) pro určení, která je správnou hodnotu pro vaši aplikaci.  
  
    > [!CAUTION]
    >  Pokud používáte [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] v sadě Visual Studio, se můžou přepsat vaše změny.  
  
## <a name="aptca"></a>APTCA  
 Otázka: Je System.Data.Linq označené k použití částečně důvěryhodným kódem?  
  
 A. Ano, knihovně System.Data.Linq.dll sestavení patří mezi ty [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] sestavení označená pomocí <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut. Bez tohoto označení, sestavení v [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] jsou určeny k použití jenom prostřednictvím plně důvěryhodného kódu.  
  
 Hlavní scénáře v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pro povolení částečně důvěryhodný volající je umožnit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sestavení, které chcete získat přístup z webových aplikací, kde *důvěryhodnosti* konfigurace je střední.  
  
## <a name="mapping-data-from-multiple-tables"></a>Mapování dat z více tabulek  
 Otázka: Data v mé entity pocházejí z více tabulek. Jak namapovat ho?  
  
 A. Můžete vytvořit zobrazení v databázi a mapovat entity do zobrazení. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje stejné SQL pro zobrazení, stejně jako u tabulek.  
  
> [!NOTE]
>  Použití zobrazení v tomto scénáři má omezení. Tento přístup funguje nejvíce bezpečně, když operace provádějí v <xref:System.Data.Linq.Table%601> jsou podporovány v podkladovém zobrazení. Víte, jenom operace, které jsou určeny. Například většina aplikací jsou jen pro čtení, a provádět jiné číslo pořádnou `Create` / `Update` / `Delete` operací pouze pomocí uložených procedur proti zobrazení.  
  
## <a name="connection-pooling"></a>Sdružování připojení  
 Otázka: Je k dispozici konstrukce, která můžou pomoct se <xref:System.Data.Linq.DataContext> sdružování?  
  
 A. Nepokoušejte se použít instance <xref:System.Data.Linq.DataContext>. Každý <xref:System.Data.Linq.DataContext> udržuje svůj stav (včetně mezipaměti identity) pro určité úpravy a dotazovat najednou. K získání nových instancí na základě aktuálního stavu databáze, použijte nové <xref:System.Data.Linq.DataContext>.  
  
 Můžete dál používat základní [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] sdružování připojení. Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="second-datacontext-is-not-updated"></a>Druhý DataContext není aktualizovaná.  
 Otázka: Můžu použít jednu instanci <xref:System.Data.Linq.DataContext> k ukládání hodnot v databázi. Ale sekundy <xref:System.Data.Linq.DataContext> ve stejné databázi neodráží aktualizovanými hodnotami. Druhá <xref:System.Data.Linq.DataContext> instance zdá se, že k vrácení hodnoty uložené v mezipaměti.  
  
 A. Toto chování je záměrné. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Vrátí stejné instance a hodnoty, které jste viděli v první instance i nadále. Když provádíte aktualizace, můžete použít optimistické řízení souběžnosti. Původní data se používají ke kontrole proti aktuální stav databáze k vyhodnocení, zda je ve skutečnosti stále beze změny. Pokud se změnila, dojde ke konfliktu a vaše aplikace musí vyřešit. Jednou z možností vaší aplikace je k obnovení původního stavu na aktuální stav databáze a opakujte aktualizaci. Další informace najdete v tématu [jak: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 Můžete také nastavit <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> na hodnotu false, která zapíná vypnout ukládání do mezipaměti a sledování změn. Poté můžete získat nejnovější hodnoty pokaždé, když odešlete dotaz.  
  
## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Nejde volat funkce SubmitChanges v režimu jen pro čtení  
 Otázka: Při pokusu o volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> v režimu jen pro čtení, se zobrazí chyba.  
  
 A. Režim jen pro čtení vypne možnost kontext sledování změn.  
  
## <a name="see-also"></a>Viz také:

- [Odkaz](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [Poradce při potížích](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)
- [Zabezpečení v LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)
