---
title: Nejčastější dotazy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 5f556c46823bd867709e8c53b59f7ac53201d242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="frequently-asked-questions"></a>Nejčastější dotazy
V následujících částech zodpovědět některé běžné problémy, které se mohou vyskytnout při implementaci [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 Další problémy jsou řešeny v [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="cannot-connect"></a>Nelze se připojit  
 OTÁZKY. Nelze se připojit k databázi.  
  
 A. Ujistěte se, že je připojovací řetězec správný a že je spuštěna instance systému SQL Server. Všimněte si také, že [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vyžaduje, aby byl povolen protokol pojmenovaných kanálů. Další informace najdete v tématu [učení podle návody](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
## <a name="changes-to-database-lost"></a>Změny databáze ztráty  
 OTÁZKY. Změny provedené k datům v databázi, ale při I reran Moje aplikace, tato změna byla již existuje.  
  
 A. Ujistěte se, že zavoláte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> výsledky uložit do databáze.  
  
## <a name="database-connection-open-how-long"></a>Připojení k databázi: Otevřete jak dlouho?  
 OTÁZKY. Jak dlouho připojení k databázi zůstanou otevřené?  
  
 A. Připojení obvykle zůstane otevřená, dokud nebude využívat výsledky dotazu. Pokud plánujete časově zpracovat všechny výsledky a jsou není nikoli ukládání do mezipaměti výsledky, použít <xref:System.Linq.Enumerable.ToList%2A> do dotazu. V běžné scénáře, kde každý objekt zpracovává jenom jednou, streamování model je nadřízená v obou `DataReader` a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Přesné údaje o využití připojení závisí na následujících:  
  
-   Stav připojení Pokud <xref:System.Data.Linq.DataContext> je vytvořený pomocí objekt připojení.  
  
-   Nastavení připojovacího řetězce (například povolení více Active výsledek sady (MARS). Další informace najdete v tématu [více sad Active výsledek (MARS)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md).  
  
## <a name="updating-without-querying"></a>Aktualizace bez dotazování  
 OTÁZKY. Můžete aktualizovat data tabulky bez první dotaz na databázi?  
  
 A. I když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemá aktualizace založená na sadu příkazů, některý z následujících postupů můžete aktualizovat bez první dotazování:  
  
-   Použití <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> k odeslání kódu SQL.  
  
-   Vytvoření nové instance objektu a inicializace všech aktuální hodnoty (pole) ovlivňující aktualizace. Pak připojte objekt, který má <xref:System.Data.Linq.DataContext> pomocí <xref:System.Data.Linq.Table%601.Attach%2A> a upravte pole, které chcete změnit.  
  
## <a name="unexpected-query-results"></a>Neočekávaný dotaz výsledky  
 OTÁZKY. Můj dotaz vrací neočekávané výsledky. Jak můžete I prohlédnout co dochází?  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje několik nástrojů pro zkontrolujete kód SQL, který generuje. Jedním z nejdůležitějších je <xref:System.Data.Linq.DataContext.Log%2A>. Další informace najdete v tématu [podpora ladění](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="unexpected-stored-procedure-results"></a>Neočekávané uložených výsledcích procedur  
 OTÁZKY. Je nutné uložené procedury, jejichž návratová hodnota je vypočítána `MAX()`. Při přetahování uložené procedury, která [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] prostor, návratová hodnota není správná.  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nabízí dva způsoby, jak vrátit generované hodnoty prostřednictvím uložené procedury:  
  
-   Pojmenováním výsledných výstupů.  
  
-   Explicitním zadáním výstupní parametr.  
  
 Následuje příklad výstupu nesprávné. Protože [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nelze mapovat na výsledcích vždy vrátí hodnotu 0:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select max(i) from t where name like 'hello'`  
  
 `end`  
  
 Následuje příklad výstupu správné v pomocí výstupní parametr:  
  
 `create procedure proc2`  
  
 `@result int OUTPUT`  
  
 `as`  
  
 `select @result = MAX(i) from t where name like 'hello'`  
  
 `go`  
  
 Následuje příklad výstupu správné v pojmenováním výsledných výstupů:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select nax(i) AS MaxResult from t where name like 'hello'`  
  
 `end`  
  
 Další informace najdete v tématu [přizpůsobení Operations podle pomocí uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md).  
  
## <a name="serialization-errors"></a>Serializace chyby  
 OTÁZKY. Při serializaci se zobrazí následující chybová zpráva: "zadejte... 'System.Data.Linq.ChangeTracker+StandardChangeTracker' není označen jako serializovatelný."  
  
 A. Generování v kódu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje <xref:System.Runtime.Serialization.DataContractSerializer> serializace. Nepodporuje <xref:System.Xml.Serialization.XmlSerializer> nebo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Další informace najdete v tématu [serializace](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md).  
  
## <a name="multiple-dbml-files"></a>Více souborů DBML  
 OTÁZKY. Při budu potřebovat více DBML souborů, které sdílejí společnou některé tabulky, zobrazí chyba kompilátoru.  
  
 A. Nastavte **kontextu Namespace** a **Entity Namespace** vlastnosti z [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] na hodnotu odlišné pro každého souboru DBML. Tento přístup eliminuje kolizí název nebo oboru názvů.  
  
## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>Zamezení explicitní nastavení generované hodnoty v příkazu Insert nebo Update  
 OTÁZKY. Je nutné databázové tabulky s `DateCreated` sloupec, který použije se výchozí hodnota SQL `Getdate()`. Při pokusu vložit nový záznam pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], získá nastaven na hodnotu `NULL`. Očekávaný by mohla být nastavenou na výchozí databázi.  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zpracuje tuto situaci automaticky pro identitu (automatického přírůstku) a rowguidcol (generované GUID) a sloupce časového razítka. V ostatních případech byste měli ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> = `true` a <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> vlastnosti.  
  
## <a name="multiple-dataloadoptions"></a>Více DataLoadOptions  
 OTÁZKY. Můžete zadat možnosti další zátěž bez přepsal první?  
  
 A. Ano. První není přepsán jako v následujícím příkladu:  
  
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
  
## <a name="errors-using-sql-compact-35"></a>Chyby jazyka SQL Compact 3.5  
 OTÁZKY. Dojde k chybě při přetahování z tabulky [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] databáze.  
  
 A. [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nepodporuje [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)], i když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemá modulu runtime. V takovém případě musíte vytvořit vlastní třídy entity a přidejte příslušné atributy.  
  
## <a name="errors-in-inheritance-relationships"></a>Chyby v dědičnosti relací  
 OTÁZKY. Použití tvaru dědičnosti sady nástrojů v [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] připojení dvě entity, ale I docházet k chybám.  
  
 A. Vytvoření relace není dost. Je třeba zadat informace, jako je například sloupce diskriminátoru, hodnota diskriminátoru základní třídy a jsou odvozené třídy diskriminátoru hodnotu.  
  
## <a name="provider-model"></a>Zprostředkovatel modelu  
 OTÁZKY. Model veřejného poskytovatele je k dispozici?  
  
 A. Bez veřejného poskytovatele modelu je k dispozici. V tomto okamžiku [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje SQL Server a [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] pouze.  
  
## <a name="sql-injection-attacks"></a>Útok prostřednictvím injektáže SQL  
 OTÁZKY. Jak je [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] chránit před útoky Injektáž SQL?  
  
 A. Injektáž SQL byl významné riziko pro tradiční dotazy SQL tvořena zřetězením vstup uživatele. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zabraňuje takové vkládání pomocí <xref:System.Data.SqlClient.SqlParameter> v dotazech. Uživatelský vstup bude převedena na hodnoty parametrů. Tento přístup škodlivý příkazy brání použití ze vstupu zákazníka.  
  
## <a name="changing-read-only-flag-in-dbml-files"></a>Změna příznak jen pro čtení ve soubory DBML  
 OTÁZKY. Jak se po vytvoření model objektů ze souboru DBML eliminovat setter z některé vlastnosti?  
  
 A. Pomocí následujících kroků pro tento scénář rozšířené:  
  
1.  V souboru DBML, upravte vlastnost změnou <xref:System.Data.Linq.ITable.IsReadOnly%2A> příznak, který `True`.  
  
2.  Přidejte konkrétní třídu. Vytvořte konstruktor s parametry pro členy jen pro čtení.  
  
3.  Zkontrolujte výchozí <xref:System.Data.Linq.Mapping.UpdateCheck> hodnotu (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) k určení, zda se jedná o správnou hodnotu pro vaši aplikaci.  
  
    > [!CAUTION]
    >  Pokud používáte [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] v sadě Visual Studio, může být přepsána změny.  
  
## <a name="aptca"></a>APTCA  
 OTÁZKY. Je System.Data.Linq označen pro použití částečně důvěryhodným kódem?  
  
 A. Ano, je sestavení knihovně System.Data.Linq.dll z těch, které [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] sestavení označené jako <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut. Bez této označení, sestavení v [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] jsou určeny k použití pouze ve plně důvěryhodný kód.  
  
 Hlavní scénáře v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pro povolení částečně důvěryhodné volající je umožnit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sestavení nelze přistupovat ze webových aplikací, kde *důvěryhodnosti* konfigurace je střední.  
  
## <a name="mapping-data-from-multiple-tables"></a>Mapování dat z více tabulek  
 OTÁZKY. Data v mé entity pocházejí z různých tabulek. Jak namapovat je?  
  
 A. Můžete vytvořit zobrazení v databázi a mapovat entitu na zobrazení. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje stejné SQL pro zobrazení jako v případě tabulek.  
  
> [!NOTE]
>  Použití zobrazení v tomto scénáři má určitá omezení. Tento postup funguje nejvíce bezpečně provést, pokud operace na <xref:System.Data.Linq.Table%601> podporuje podkladového zobrazení. Pouze víte operací, které jsou určené. Například většina aplikací jsou jen pro čtení, a provádět jiné výraznou číslo `Create` / `Update` / `Delete` operací pouze pomocí uložené procedury proti zobrazení.  
  
## <a name="connection-pooling"></a>Sdružování připojení  
 OTÁZKY. Je k dispozici konstrukce, které vám pomohou při <xref:System.Data.Linq.DataContext> sdružování?  
  
 A. Nepokoušejte se použít instancí <xref:System.Data.Linq.DataContext>. Každý <xref:System.Data.Linq.DataContext> Udržovat stav (včetně mezipaměti identity) pro jednu relaci konkrétní upravit nebo dotazu. Chcete-li získat nové instance na základě aktuálního stavu databáze, použijte nové <xref:System.Data.Linq.DataContext>.  
  
 Můžete dál používat základní [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] sdružování připojení. Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="second-datacontext-is-not-updated"></a>Druhý DataContext se neaktualizuje  
 OTÁZKY. Mohu použít jednu instanci <xref:System.Data.Linq.DataContext> pro uložení hodnot v databázi. Ale druhý <xref:System.Data.Linq.DataContext> na stejnou databázi nezohledňuje aktualizovanými hodnotami. Druhý <xref:System.Data.Linq.DataContext> instance zdá se, že k návratu hodnot v mezipaměti.  
  
 A. Toto chování je záměrné. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nadále vrátí stejné instance nebo hodnoty, které jste viděli v první instance. Pokud provedete aktualizace, je použít optimistickou metodu souběžného. Původní data se používá ke kontrole proti aktuální stav databáze k vyhodnocení, zda je ve skutečnosti stále beze změny. Pokud se změnila, dojde ke konfliktu a aplikace ho musí vyřešit. Jednou z možností aplikace je potřeba obnovit původní stav aktuální stav databáze a opakujte aktualizaci. Další informace najdete v tématu [postupy: Správa konfliktů změnu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 Můžete také nastavit <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> na hodnotu false, které oplátku vypnout ukládání do mezipaměti a sledování změn. Poté můžete získat nejnovější hodnoty pokaždé, když dotazujete.  
  
## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Nelze volat SubmitChanges v režimu jen pro čtení  
 OTÁZKY. Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> v režimu jen pro čtení, zobrazí chybová zpráva.  
  
 A. Jen pro čtení režimu vypne schopnost kontext sledování změn.  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Odstraňování potíží](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)  
 [Zabezpečení v LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)
