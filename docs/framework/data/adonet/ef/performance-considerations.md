---
title: Požadavky na výkon (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: eb46b183ec1e930dfe5c4a1eea237024033c357d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854598"
---
# <a name="performance-considerations-entity-framework"></a>Požadavky na výkon (Entity Framework)
Toto téma popisuje charakteristiky výkonu ADO.NET Entity Framework a poskytuje několik důležitých informací, které vám pomůžou zlepšit výkon Entity Framework aplikací.  
  
## <a name="stages-of-query-execution"></a>Fáze provádění dotazů  
 Aby bylo možné lépe pochopit výkon dotazů v Entity Framework, je užitečné pochopit operace, ke kterým dochází, když se dotaz spustí na koncepčním modelu a vrátí data jako objekty. Následující tabulka popisuje tento sled operací.  
  
|Operace|Relativní náklady|Frekvence|Komentáře|  
|---------------|-------------------|---------------|--------------|  
|Načítají se metadata.|Mírná|Jednou v každé doméně aplikace.|Metadata modelu a mapování používaná Entity Framework jsou načtena do <xref:System.Data.Metadata.Edm.MetadataWorkspace>. Tato metadata jsou v mezipaměti globálně a jsou k dispozici pro <xref:System.Data.Objects.ObjectContext> jiné instance ve stejné aplikační doméně.|  
|Otevírání připojení k databázi|Střední<sup>1</sup>|Podle potřeby.|Vzhledem k tomu, že otevřené připojení k databázi spotřebovává cenný prostředek, Entity Framework otevře a zavře připojení databáze pouze podle potřeby. Připojení můžete také explicitně otevřít. Další informace najdete v tématu [Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).|  
|Generování zobrazení|Vysoká|Jednou v každé doméně aplikace. (Může být vygenerováno předem.)|Předtím, než Entity Framework může spustit dotaz na koncepční model nebo uložit změny do zdroje dat, je nutné pro přístup k databázi vygenerovat sadu zobrazení místních dotazů. Kvůli vysokým nákladům na generování těchto zobrazení můžete zobrazení předem vygenerovat a přidat je do projektu v době návrhu. Další informace najdete v tématu [jak: Předem vygenerujte zobrazení pro zlepšení výkonu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))dotazů.|  
|Příprava dotazu|Střední<sup>2</sup>|Jednou pro každý jedinečný dotaz.|Zahrnuje náklady na vytvoření příkazu dotazu, vygenerování stromu příkazů na základě modelu a mapování metadat a definování tvaru vrácených dat. Vzhledem k tomu, že Entity SQL příkazy dotazů a dotazy LINQ jsou ukládány do mezipaměti, pozdější spuštění stejného dotazu trvá méně času. Můžete přesto použít zkompilované dotazy LINQ k omezení těchto nákladů v pozdějším spuštění a zkompilované dotazy mohou být efektivnější než dotazy LINQ, které jsou automaticky uloženy v mezipaměti. Další informace najdete v tématu [kompilované dotazy (LINQ to Entities)](./language-reference/compiled-queries-linq-to-entities.md). Obecné informace o provádění dotazů LINQ naleznete v tématu [LINQ to Entities](./language-reference/linq-to-entities.md). **Poznámka:**  LINQ to Entities dotazy, které aplikují `Enumerable.Contains` operátor na kolekce v paměti, nejsou automaticky ukládány do mezipaměti. V kompilovaných dotazech LINQ se taky Parametrizace kolekce v paměti, které se nepovolují.|  
|Provádění dotazu|Nízká úroveň<sup>2</sup>|Jednou pro každý dotaz.|Náklady na provedení příkazu proti zdroji dat pomocí poskytovatele dat ADO.NET. Vzhledem k tomu, že většina zdrojů dat ukládá plány dotazů do mezipaměti, může pozdější spuštění stejného dotazu trvat i kratší dobu.|  
|Načítání a ověřování typů|Nízká úroveň<sup>3</sup>|Jednou pro každou <xref:System.Data.Objects.ObjectContext> instanci.|Typy jsou načteny a ověřovány proti typům, které definuje koncepční model.|  
|Sledování|Nízká úroveň<sup>3</sup>|Jednou pro každý objekt, který dotaz vrátí. <sup>4</sup>|Pokud dotaz používá možnost sloučení <xref:System.Data.Objects.MergeOption.NoTracking> , tato fáze nemá vliv na výkon.<br /><br /> Pokud <xref:System.Data.Objects.MergeOption.AppendOnly>dotaz používá <xref:System.Data.Objects.MergeOption.PreserveChanges> možnost,<xref:System.Data.Objects.MergeOption.OverwriteChanges> nebo sloučení, výsledky dotazu jsou sledovány v. <xref:System.Data.Objects.ObjectStateManager> Vygeneruje <xref:System.Data.Objects.ObjectStateEntry> <xref:System.Data.Objects.ObjectStateManager>se pro každý sledovaný objekt, který dotaz vrátí a který se použije k vytvoření v. <xref:System.Data.EntityKey> Pokud je nalezen <xref:System.Data.Objects.ObjectStateEntry> existující objekt <xref:System.Data.EntityKey>pro, je vrácen existující objekt. Je-li použita <xref:System.Data.Objects.MergeOption.OverwriteChanges> možnost nebo, je objekt aktualizován před jeho vrácením. <xref:System.Data.Objects.MergeOption.PreserveChanges><br /><br /> Další informace najdete v tématu věnovaném [rozlišení identity, správě stavů a Change Tracking](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
|Vyhodnocování objektů|Střední<sup>3</sup>|Jednou pro každý objekt, který dotaz vrátí. <sup>4</sup>|Proces čtení vráceného <xref:System.Data.Common.DbDataReader> objektu a vytváření objektů a nastavení hodnot vlastností, které jsou založeny na hodnotách v jednotlivých instancích <xref:System.Data.Common.DbDataRecord> třídy. Pokud objekt již existuje v <xref:System.Data.Objects.ObjectContext> a dotaz používá možnosti nebo <xref:System.Data.Objects.MergeOption.PreserveChanges> sloučení, <xref:System.Data.Objects.MergeOption.AppendOnly> Tato fáze nemá vliv na výkon. Další informace najdete v tématu věnovaném [rozlišení identity, správě stavů a Change Tracking](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
  
 <sup>1</sup> když zprostředkovatel zdroje dat implementuje sdružování připojení, náklady na otevření připojení se napříč fondem rozdělují. Zprostředkovatel rozhraní .NET pro SQL Server podporuje sdružování připojení.  
  
 <sup>2</sup> náklady se zvyšují se zvýšením složitosti dotazů.  
  
 <sup>3</sup> celkové náklady se zvyšují úměrně k počtu objektů vrácených dotazem.  
  
 <sup>4</sup> tato režie není pro dotazy EntityClient nutná, protože dotazy EntityClient vracejí <xref:System.Data.EntityClient.EntityDataReader> místo objektů. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Další požadavky  
 Následují další skutečnosti, které mohou ovlivnit výkon aplikací Entity Framework.  
  
### <a name="query-execution"></a>Provádění dotazů  
 Vzhledem k tomu, že dotazy můžou být náročné na prostředky, zvažte, v jakém místě v kódu a na jakém počítači se dotaz spustí.  
  
#### <a name="deferred-versus-immediate-execution"></a>Odložené versus okamžité provedení  
 Při vytváření <xref:System.Data.Objects.ObjectQuery%601> dotazu LINQ se dotaz nemůže spustit okamžitě. Provádění dotazu `foreach` je odloženo, dokud nebudou požadovány výsledky, například během výčtu (C#) nebo `For Each` (Visual Basic) nebo <xref:System.Collections.Generic.List%601> když je přiřazen k vyplňování kolekce. Spuštění dotazu začíná ihned při <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> volání metody <xref:System.Data.Objects.ObjectQuery%601> na nebo při volání metody LINQ, která vrací dotaz typu <xref:System.Linq.Enumerable.First%2A> singleton, například nebo <xref:System.Linq.Enumerable.Any%2A>. Další informace najdete v tématu [dotazy objektů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)) a [provádění dotazů (LINQ to Entities)](./language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>Spuštění dotazů LINQ na straně klienta  
 I když se spustí dotaz LINQ v počítači, který je hostitelem zdroje dat, mohou být některé části dotazu LINQ vyhodnoceny v klientském počítači. Další informace najdete v části spuštění úložiště v tématu [spuštění dotazu (LINQ to Entities)](./language-reference/query-execution.md).  
  
### <a name="query-and-mapping-complexity"></a>Složitost dotazů a mapování  
 Složitost jednotlivých dotazů a mapování v modelu entity model bude mít výrazný vliv na výkon dotazů.  
  
#### <a name="mapping-complexity"></a>Složitost mapování  
 Modely, které jsou složitější než jednoduché mapování 1:1 mezi entitami v koncepčním modelu a tabulkách v modelu úložiště, generují složitější příkazy než modely, které mají mapování 1:1.  
  
#### <a name="query-complexity"></a>Složitost dotazů  
 Dotazy, které vyžadují velký počet spojení v příkazech, které jsou spouštěny proti zdroji dat nebo které vracejí velké množství dat, mohou ovlivnit výkon následujícími způsoby:  
  
- Dotazy na koncepční model, který vypadá jako jednoduchý, mohou vést k provádění složitějších dotazů na zdroj dat. K tomu může dojít, protože Entity Framework transformuje dotaz na koncepční model na ekvivalentní dotaz na zdroj dat. Pokud je jedna entita sady v koncepčním modelu mapována na více než jednu tabulku ve zdroji dat nebo pokud je relace mezi entitami namapována na tabulku spojení, příkaz dotazu spuštěný proti dotazu zdroje dat může vyžadovat jedno nebo více spojení.  
  
    > [!NOTE]
    > <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> Použijte metodu<xref:System.Data.Objects.ObjectQuery%601> třídy nebo<xref:System.Data.EntityClient.EntityCommand> pro zobrazení příkazů, které jsou spouštěny proti zdroji dat pro daný dotaz. Další informace najdete v tématu [jak: Zobrazit příkazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100))úložiště  
  
- Vnořené Entity SQL dotazy mohou vytvořit spojení na serveru a mohou vracet velký počet řádků.  
  
     Následuje příklad vnořeného dotazu v klauzuli projekce:  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Tyto dotazy navíc způsobí, že kanál dotazu vygeneruje jediný dotaz s duplicitou objektů napříč vnořenými dotazy. Z tohoto důvodu může být jeden sloupec vícekrát duplikován. V některých databázích, včetně SQL Server, to může způsobit, že se tabulka TempDB zvětší velmi velká, což může snížit výkon serveru. Při provádění vnořených dotazů by měla být provedena péče.  
  
- Všechny dotazy, které vracejí velké množství dat, mohou způsobit snížení výkonu, pokud klient provádí operace, které spotřebovávají prostředky způsobem, který je úměrný velikosti sady výsledků dotazu. V takových případech byste měli zvážit omezení množství dat vrácených dotazem. Další informace najdete v tématu [jak: Stránky prostřednictvím výsledků](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))dotazu.  
  
 Příkazy automaticky generované Entity Framework můžou být složitější než podobné příkazy zapsané explicitně vývojářem databáze. Pokud potřebujete explicitní kontrolu nad příkazy provedenými na zdroji dat, zvažte definování mapování na funkci vracející tabulku nebo uloženou proceduru.  
  
#### <a name="relationships"></a>Relace  
 Pro zajištění optimálního výkonu dotazů je nutné definovat vztahy mezi entitami jako asociace v modelu entity a jako logické vztahy ve zdroji dat.  
  
### <a name="query-paths"></a>Cesty k dotazům  
 Ve výchozím nastavení se při spuštění <xref:System.Data.Objects.ObjectQuery%601>nevrátí související objekty (i když objekty reprezentující samotné relace jsou). Související objekty můžete načítat jedním ze tří způsobů:  
  
1. Nastavte cestu k dotazu před <xref:System.Data.Objects.ObjectQuery%601> provedením příkazu.  
  
2. `Load` Volejte metodu pro navigační vlastnost, kterou objekt zpřístupňuje.  
  
3. <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> Nastavte možnost<xref:System.Data.Objects.ObjectContext> na .`true` Všimněte si, že to je provedeno automaticky při generování kódu objektové vrstvy pomocí [návrháře model EDM (Entity Data Model)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)). Další informace najdete v tématu [Přehled generovaného kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982041(v=vs.100)).  
  
 Pokud se rozhodnete, kterou možnost použijete, mějte na paměti, že mezi počtem požadavků na databázi a množstvím dat vráceným v jednom dotazu dojde k kompromisům. Další informace najdete v tématu [načítání souvisejících objektů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
#### <a name="using-query-paths"></a>Použití cest dotazů  
 Cesty k dotazům definují graf objektů, které dotaz vrátí. Pokud definujete cestu k dotazu, je vyžadována pouze jedna žádost vůči databázi, aby vracela všechny objekty, které tato cesta definuje. Použití cest dotazů může vést k tomu, že se u zdroje dat spustí složité příkazy z zdánlivě jednoduchých dotazů na objekty. K tomu dochází, protože k vrácení souvisejících objektů v jednom dotazu je potřeba jedna nebo víc spojení. Tato složitost je větší v dotazech na model komplexní entity, jako je například entita s děděním nebo cesta, která obsahuje relace m:n.  
  
> [!NOTE]
> Použijte metodu k zobrazení příkazu, který bude vygenerován <xref:System.Data.Objects.ObjectQuery%601>pomocí. <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> Další informace najdete v tématu [jak: Zobrazit příkazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100))úložiště  
  
 Pokud cesta k dotazu obsahuje příliš mnoho souvisejících objektů nebo objekty obsahují příliš mnoho dat řádku, zdroj dat nemusí být schopen dotaz dokončit. K tomu dojde, pokud dotaz vyžaduje přechodné dočasné úložiště, které překračuje možnosti zdroje dat. Pokud k tomu dojde, můžete zjednodušit složitost dotazu zdroje dat tím, že explicitně načítajíte související objekty.  
  
#### <a name="explicitly-loading-related-objects"></a>Explicitní načítání souvisejících objektů  
 Související objekty lze explicitně načíst voláním `Load` metody pro vlastnost navigace, která <xref:System.Data.Objects.DataClasses.EntityCollection%601> vrací nebo <xref:System.Data.Objects.DataClasses.EntityReference%601>. Explicitní načítání objektů vyžaduje, aby se databáze pokaždé volala při `Load` každém volání.  
  
> [!NOTE]
> Pokud voláte `Load` při opakování kolekce vrácených objektů, například při `foreach` použití příkazu (`For Each` v Visual Basic), musí zprostředkovatel specifických zdrojů dat podporovat více aktivních sad výsledků na jednom vázán. `MultipleActiveResultSets = true` V případě databáze SQL Server musíte zadat hodnotu v připojovacím řetězci zprostředkovatele.  
  
 Tuto <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> metodu můžete použít také v případě, že entity <xref:System.Data.Objects.DataClasses.EntityCollection%601> nejsou <xref:System.Data.Objects.DataClasses.EntityReference%601> žádné nebo vlastnosti. To je užitečné při používání entit POCO.  
  
 I když se explicitně načítají související objekty, sníží se počet spojení a sníží množství redundantních dat `Load` , vyžaduje opakovaná připojení k databázi, což může být nákladné při explicitním načítání velkého počtu objektů.  
  
### <a name="saving-changes"></a>Uložení změn  
 Při volání <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metody <xref:System.Data.Objects.ObjectContext>na, je vygenerován samostatný příkaz CREATE, Update nebo DELETE pro všechny přidávané, aktualizované nebo odstraněné objekty v kontextu. Tyto příkazy jsou spouštěny ve zdroji dat v rámci jedné transakce. Stejně jako u dotazů je výkon operací vytvoření, aktualizace a odstranění závislý na složitosti mapování v koncepčním modelu.  
  
### <a name="distributed-transactions"></a>Distribuované transakce  
 Operace v explicitní transakci, která vyžaduje prostředky spravované službou DTC (Distributed Transaction Coordinator), budou mnohem dražší než podobná operace, která nevyžaduje službu DTC. K povýšení služby DTC dojde v následujících situacích:  
  
- Explicitní transakce s operací s databází SQL Server 2000 nebo jiným zdrojem dat, která vždy propaguje explicitní transakce do služby DTC.  
  
- Explicitní transakce s operací s SQL Server 2005, pokud je připojení spravováno Entity Framework. K tomu dochází, protože SQL Server 2005 se propaguje k DTC při každém zavření a opětovném otevření připojení v rámci jedné transakce, což je výchozí chování Entity Framework. Tato propagace služby DTC se nevyskytuje při použití SQL Server 2008. Chcete-li se vyhnout této povýšení při použití SQL Server 2005, je nutné explicitně otevřít a zavřít připojení v rámci transakce. Další informace najdete v tématu [Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
 Explicitní transakce se používá v případě, že se v <xref:System.Transactions> transakci spustí jedna nebo více operací. Další informace najdete v tématu [Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="strategies-for-improving-performance"></a>Strategie pro zlepšení výkonu  
 Můžete zvýšit celkový výkon dotazů v Entity Framework pomocí následujících strategií.  
  
#### <a name="pre-generate-views"></a>Předem generovat zobrazení  
 Generování zobrazení založeného na modelu entity je významné náklady, při kterých aplikace spouští dotaz poprvé. Pomocí nástroje EdmGen. exe předem vygenerujte zobrazení jako Visual Basic nebo C# soubor kódu, který lze přidat do projektu během návrhu. Můžete také použít sadu text Template Transform Toolkit k vygenerování předem kompilovaných zobrazení. Předem vygenerovaná zobrazení jsou ověřována za běhu, aby se zajistilo, že jsou v souladu s aktuální verzí zadaného modelu entity. Další informace najdete v tématu [jak: Předem vygenerujte zobrazení pro zlepšení výkonu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))dotazů.
  
 Při práci s velmi velkými modely platí následující aspekty:  
  
 Formát metadat .NET omezuje počet znaků uživatelského řetězce v daném binárním formátu na 16 777 215 (0xFFFFFF). Pokud generujete zobrazení pro velmi velký model a zobrazení souborů dosáhne tohoto limitu velikosti, zobrazí se při vytváření dalších uživatelských řetězců nezbývá žádné logické místo. Chyba kompilace Toto omezení velikosti se vztahuje na všechny spravované binární soubory. Další informace najdete v [blogu](https://go.microsoft.com/fwlink/?LinkId=201476) , který ukazuje, jak se vyhnout chybě při práci s velkými a složitými modely.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Zvažte použití možnosti sloučení NoTracking pro dotazy  
 Ke sledování vrácených objektů v kontextu objektu je nutné mít náklady. Zjišťování změn objektů a zajištění, že více požadavků pro stejnou logickou entitu vrací stejnou instanci objektu, vyžaduje, aby byly objekty připojeny <xref:System.Data.Objects.ObjectContext> k instanci. Pokud neplánujete provádět aktualizace nebo odstraňování objektů a nepožadujete správu identit, zvažte použití <xref:System.Data.Objects.MergeOption.NoTracking> možností sloučení při spouštění dotazů.  
  
#### <a name="return-the-correct-amount-of-data"></a>Vrátí správné množství dat.  
 V některých scénářích je zadání cesty k dotazu pomocí <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metody mnohem rychlejší, protože vyžaduje méně přenosných cest k databázi. Nicméně v jiných scénářích může být další operace zpoždění při načítání souvisejících objektů rychlejší, protože jednodušší dotazy s menším počtem spojení mají za následek menší redundanci dat. Z tohoto důvodu doporučujeme, abyste otestovali výkon různých způsobů načítání souvisejících objektů. Další informace najdete v tématu [načítání souvisejících objektů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
 Aby nedošlo k vrácení příliš velkého množství dat v jednom dotazu, zvažte možnost stránkování výsledků dotazu do více spravovatelných skupin. Další informace najdete v tématu [jak: Stránky prostřednictvím výsledků](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))dotazu.  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>Omezení rozsahu objektu ObjectContext  
 Ve většině případů byste měli vytvořit <xref:System.Data.Objects.ObjectContext> instanci `using` v rámci příkazu (`Using…End Using` v Visual Basic). To může zvýšit výkon tím, že zajistí, že prostředky asociované s kontextem objektu jsou uvolněny automaticky, když kód ukončí blok příkazu. Nicméně pokud jsou ovládací prvky svázány s objekty, které jsou spravovány kontextem objektu, <xref:System.Data.Objects.ObjectContext> měla by být instance udržována tak dlouho, dokud je vazba zapotřebí a uvolněna ručně. Další informace najdete v tématu [Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Zvažte ruční otevření připojení k databázi.  
 Když vaše aplikace provede řadu dotazů na objekty nebo často volání <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> k uchování operací vytvoření, aktualizace a odstranění na zdroj dat, Entity Framework musí nepřetržitě otevřít a zavřít připojení ke zdroji dat. V těchto situacích zvažte ruční otevření připojení na začátku těchto operací a buď uzavření nebo zrušení připojení po dokončení operací. Další informace najdete v tématu [Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="performance-data"></a>Údaje o výkonu  
 Některá data o výkonu pro Entity Framework jsou publikována v následujících příspěvcích na [blogu týmu ADO.NET](https://go.microsoft.com/fwlink/?LinkId=91905):  
  
- [Zkoumání výkonu ADO.NET Entity Framework – část 1](https://go.microsoft.com/fwlink/?LinkId=123907)  
  
- [Zkoumání výkonu ADO.NET Entity Framework – část 2](https://go.microsoft.com/fwlink/?LinkId=123909)  
  
- [Porovnání výkonu ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o vývoji a nasazení](development-and-deployment-considerations.md)
