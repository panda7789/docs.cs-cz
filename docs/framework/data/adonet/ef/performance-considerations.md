---
title: Důležité informace o výkonu (entity Framework)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: 0ff018fe0d8199dcd790bcd3de18751662e0a92b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149736"
---
# <a name="performance-considerations-entity-framework"></a>Důležité informace o výkonu (entity Framework)
Toto téma popisuje charakteristiky výkonu ADO.NET entity framework a poskytuje některé důležité informace, které pomáhají zlepšit výkon aplikací entity framework.  
  
## <a name="stages-of-query-execution"></a>Fáze provádění dotazů  
 Chcete-li lépe porozumět výkonu dotazů v rámci entity, je užitečné pochopit operace, ke kterým dochází při spuštění dotazu proti konceptuálnímu modelu a vrátí data jako objekty. Následující tabulka popisuje tuto řadu operací.  
  
|Operace|Relativní náklady|Frequency|Komentáře|  
|---------------|-------------------|---------------|--------------|  
|Načítání metadat|Střední|Jednou v každé doméně aplikace.|Model a mapování metadat používaných entity framework <xref:System.Data.Metadata.Edm.MetadataWorkspace>se načte do . Tato metadata jsou globálně uložena v mezipaměti <xref:System.Data.Objects.ObjectContext> a jsou k dispozici pro ostatní instance ve stejné doméně aplikace.|  
|Otevření připojení k databázi|Střední<sup>1</sup>|Podle potřeby.|Vzhledem k tomu, že otevřené připojení k databázi spotřebovává cenný prostředek, entity framework otevře a zavře připojení databáze pouze podle potřeby. Připojení můžete také explicitně otevřít. Další informace naleznete v [tématu Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).|  
|Generování zobrazení|Vysoká|Jednou v každé doméně aplikace. (Lze předem vygenerovat.)|Před entity Framework můžete spustit dotaz proti koncepční model nebo uložit změny do zdroje dat, musí generovat sadu místních zobrazení dotazu pro přístup k databázi. Vzhledem k vysokým nákladům na generování těchto zobrazení můžete předem vygenerovat zobrazení a přidat je do projektu v době návrhu. Další informace naleznete v [tématu How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).|  
|Příprava dotazu|Střední<sup>2</sup>|Jednou pro každý jedinečný dotaz.|Zahrnuje náklady na vytvoření příkazu dotazu, generování stromu příkazů na základě modelu a mapování metadat a definování tvaru vrácených dat. Protože nyní jsou příkazy dotazu ENTITY SQL a dotazy LINQ uloženy v mezipaměti, pozdější spuštění stejného dotazu zabere méně času. Stále můžete použít kompilované LINQ dotazy ke snížení těchto nákladů v pozdějších spuštěnía a zkompilované dotazy mohou být efektivnější než linq dotazy, které jsou automaticky ukládány do mezipaměti. Další informace naleznete [v tématu Kompilované dotazy (LINQ na entity).](./language-reference/compiled-queries-linq-to-entities.md) Obecné informace o spuštění dotazu LINQ naleznete v tématu [LINQ to Entities](./language-reference/linq-to-entities.md). **Poznámka:**  LINQ na entity dotazy, `Enumerable.Contains` které platí operátor v kolekcích v paměti nejsou automaticky ukládány do mezipaměti. Také parametrizace in-memory kolekce v kompilovaných linq dotazů není povoleno.|  
|Spuštění dotazu|Nízká<sup>2</sup>|Jednou pro každý dotaz.|Náklady na provedení příkazu proti zdroji dat pomocí zprostředkovatele dat ADO.NET. Vzhledem k tomu, že většina zdrojů dat ukládá plány dotazů do mezipaměti, může pozdější spuštění stejného dotazu trvat ještě méně času.|  
|Načítání a ověřování typů|Nízká<sup>3</sup>|Jednou pro <xref:System.Data.Objects.ObjectContext> každou instanci.|Typy jsou načteny a ověřeny proti typy, které definuje koncepční model.|  
|Sledování|Nízká<sup>3</sup>|Jednou pro každý objekt, který vrátí dotaz. <sup>4</sup>|Pokud dotaz používá <xref:System.Data.Objects.MergeOption.NoTracking> možnost sloučení, tato fáze nemá vliv na výkon.<br /><br /> Pokud dotaz používá <xref:System.Data.Objects.MergeOption.AppendOnly> <xref:System.Data.Objects.MergeOption.PreserveChanges>možnost <xref:System.Data.Objects.MergeOption.OverwriteChanges> , nebo sloučení, jsou výsledky <xref:System.Data.Objects.ObjectStateManager>dotazu sledovány v aplikaci . Je <xref:System.Data.EntityKey> generován pro každý sledovaný objekt, který dotaz vrátí <xref:System.Data.Objects.ObjectStateEntry> a <xref:System.Data.Objects.ObjectStateManager>slouží k vytvoření v . Pokud existující <xref:System.Data.Objects.ObjectStateEntry> lze nalézt <xref:System.Data.EntityKey>pro , je vrácen existující objekt. Pokud <xref:System.Data.Objects.MergeOption.PreserveChanges>je <xref:System.Data.Objects.MergeOption.OverwriteChanges> použita možnost , nebo, objekt je aktualizován před jeho vrácení.<br /><br /> Další informace naleznete [v tématu Rozlišení identity, Správa stavu a Sledování změn](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
|Zhmotnění objektů|Střední<sup>3</sup>|Jednou pro každý objekt, který vrátí dotaz. <sup>4</sup>|Proces čtení vráceného <xref:System.Data.Common.DbDataReader> objektu a vytváření objektů a nastavení hodnot vlastností, <xref:System.Data.Common.DbDataRecord> které jsou založeny na hodnotách v každé instanci třídy. Pokud objekt již existuje <xref:System.Data.Objects.ObjectContext> v a dotaz <xref:System.Data.Objects.MergeOption.AppendOnly> <xref:System.Data.Objects.MergeOption.PreserveChanges> používá možnosti nebo sloučení, tato fáze nemá vliv na výkon. Další informace naleznete [v tématu Rozlišení identity, Správa stavu a Sledování změn](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
  
 <sup>1</sup> Když zprostředkovatel zdroje dat implementuje sdružování připojení, náklady na otevření připojení jsou distribuovány v rámci fondu. Zprostředkovatel rozhraní .NET pro sql server podporuje sdružování připojení.  
  
 <sup>2</sup> Náklady se zvyšují se zvýšenou složitostí dotazu.  
  
 <sup>3</sup> Celkové náklady se zvýší úměrně počtu objektů vrácených dotazem.  
  
 <sup>4</sup> Tato režie není vyžadována pro dotazy EntityClient, <xref:System.Data.EntityClient.EntityDataReader> protože dotazy EntityClient vrátí místo objektů. Další informace naleznete [v tématu EntityClient Provider for the Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Další důležité informace  
 Následují další důležité informace, které mohou ovlivnit výkon aplikací entity framework.  
  
### <a name="query-execution"></a>Provádění dotazů  
 Vzhledem k tomu, že dotazy mohou být náročné na prostředky, zvažte, v jakém okamžiku v kódu a na jakém počítači je dotaz spuštěn.  
  
#### <a name="deferred-versus-immediate-execution"></a>Odložené versus okamžité provedení  
 Při vytváření <xref:System.Data.Objects.ObjectQuery%601> dotazu nebo LINQ dotaz nemusí být spuštěn okamžitě. Spuštění dotazu je odloženo, dokud jsou `foreach` potřebné výsledky, `For Each` například během (C#) nebo (Visual <xref:System.Collections.Generic.List%601> Basic) výčtu nebo při přiřazení k vyplnění kolekce. Spuštění dotazu začíná okamžitě <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> při volání <xref:System.Data.Objects.ObjectQuery%601> metody na nebo při volání LINQ metoda, která <xref:System.Linq.Enumerable.First%2A> <xref:System.Linq.Enumerable.Any%2A>vrací omílaný dotaz, například nebo . Další informace naleznete [v tématu Dotazy na objekty](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)) a [provádění dotazů (LINQ na entity).](./language-reference/query-execution.md)  
  
#### <a name="client-side-execution-of-linq-queries"></a>Provádění dotazů LINQ na straně klienta  
 Přestože dojde k provedení dotazu LINQ v počítači, který je hostitelem zdroje dat, některé části dotazu LINQ mohou být vyhodnoceny v klientském počítači. Další informace naleznete v části Spuštění úložiště [spuštění dotazu (LINQ na entity).](./language-reference/query-execution.md)  
  
### <a name="query-and-mapping-complexity"></a>Složitost dotazů a mapování  
 Složitost jednotlivých dotazů a mapování v modelu entity bude mít významný vliv na výkon dotazu.  
  
#### <a name="mapping-complexity"></a>Složitost mapování  
 Modely, které jsou složitější než jednoduché mapování 1:1 mezi entitami v koncepčním modelu a tabulkami v modelu úložiště, generují složitější příkazy než modely, které mají mapování 1:1.  
  
#### <a name="query-complexity"></a>Složitost dotazu  
 Dotazy, které vyžadují velký počet spojení v příkazech, které jsou provedeny proti zdroji dat nebo které vracejí velké množství dat, mohou ovlivnit výkon následujícími způsoby:  
  
- Dotazy proti koncepční model, který se zdají jednoduché může mít za následek provádění složitější dotazy proti zdroj dat. K tomu může dojít, protože entity Framework překládá dotaz proti konceptuální model do ekvivalentní dotaz proti zdroj dat. Pokud se jedna entita nastavená v koncepčním modelu mapuje na více než jednu tabulku ve zdroji dat nebo když je relace mezi entitami mapována na tabulku spojení, může příkaz dotazu spuštěný proti dotazu zdroje dat vyžadovat jedno nebo více spojení.  
  
    > [!NOTE]
    > Pomocí <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metody <xref:System.Data.Objects.ObjectQuery%601> or <xref:System.Data.EntityClient.EntityCommand> třídy můžete zobrazit příkazy, které jsou provedeny proti zdroji dat pro daný dotaz. Další informace naleznete v [tématu How to: View the Store Commands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
- Vnořené entity SQL dotazy může vytvářet spojení na serveru a může vrátit velký počet řádků.  
  
     Následuje příklad vnořeného dotazu v projekční klauzuli:  
  
    ```sql  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Kromě toho tyto dotazy způsobit kanálu dotazu generovat jeden dotaz s duplikací objektů přes vnořené dotazy. Z tohoto důvodu jeden sloupec může být duplikována vícekrát. V některých databázích, včetně SQL Server, to může způsobit, že tabulka TempDB růst velmi velké, což může snížit výkon serveru. Při provádění vnořených dotazů je třeba dbát na to, aby byla přijata pozornost.  
  
- Všechny dotazy, které vracejí velké množství dat může způsobit snížení výkonu, pokud klient provádí operace, které spotřebovávají prostředky způsobem, který je úměrný velikosti sady výsledků. V takových případech byste měli zvážit omezení množství dat vrácených dotazem. Další informace naleznete v [tématu How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
 Všechny příkazy automaticky generované entity framework může být složitější než podobné příkazy napsané explicitně vývojář databáze. Pokud potřebujete explicitní kontrolu nad příkazy spuštěnými proti zdroji dat, zvažte definování mapování na funkci s hodnotou tabulky nebo uloženou proceduru.  
  
#### <a name="relationships"></a>Relace  
 Pro optimální výkon dotazu je nutné definovat vztahy mezi entitami jako přidružení v modelu entity i jako logické vztahy ve zdroji dat.  
  
### <a name="query-paths"></a>Cesty k dotazu  
 Ve výchozím nastavení při <xref:System.Data.Objects.ObjectQuery%601>spuštění nejsou vráceny související objekty (i když objekty, které představují samotné vztahy jsou). Související objekty můžete načíst jedním ze tří způsobů:  
  
1. Nastavte cestu dotazu <xref:System.Data.Objects.ObjectQuery%601> před spuštěním.  
  
2. Volání `Load` metody na navigační vlastnost, která objekt zveřejňuje.  
  
3. Nastavte <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> možnost na <xref:System.Data.Objects.ObjectContext> `true`na . Všimněte si, že se to provádí automaticky při generování kódu objektové vrstvy pomocí [návrháře datového modelu entit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)). Další informace naleznete [v tématu Přehled generovaného kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982041(v=vs.100)).  
  
 Pokud vezmete v úvahu, kterou možnost použít, uvědomte si, že existuje kompromis mezi počtem požadavků proti databázi a množstvím dat vrácených v jednom dotazu. Další informace naleznete v [tématu Načítání souvisejících objektů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
#### <a name="using-query-paths"></a>Použití cest dotazu  
 Cesty dotazu definují graf objektů, které dotaz vrací. Když definujete cestu dotazu, pouze jeden požadavek proti databázi je nutné vrátit všechny objekty, které definuje cestu. Použití cest dotazu může mít za následek složité příkazy, které jsou spouštěny proti zdroji dat ze zdánlivě jednoduchých dotazů na objekty. K tomu dochází, protože jeden nebo více spojení jsou nutné vrátit související objekty v jednom dotazu. Tato složitost je větší v dotazech proti modelu složitých entit, jako je entita s dědičností nebo cesta, která zahrnuje relace N:N.  
  
> [!NOTE]
> Pomocí <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metody můžete zobrazit příkaz, který bude <xref:System.Data.Objects.ObjectQuery%601>generován pomocí příkazu . Další informace naleznete v [tématu How to: View the Store Commands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
 Pokud cesta k dotazu obsahuje příliš mnoho souvisejících objektů nebo objekty obsahují příliš mnoho dat řádků, zdroj dat pravděpodobně nebude schopen dokončit dotaz. K tomu dochází, pokud dotaz vyžaduje zprostředkující dočasné úložiště, které překračuje možnosti zdroje dat. V takovém případě můžete snížit složitost dotazu zdroje dat explicitnínačítání souvisejících objektů.  
  
#### <a name="explicitly-loading-related-objects"></a>Explicitní načítání souvisejících objektů  
 Související objekty můžete explicitně `Load` načíst voláním metody <xref:System.Data.Objects.DataClasses.EntityCollection%601> <xref:System.Data.Objects.DataClasses.EntityReference%601>na navigační vlastnosti, která vrací vlastnost nebo . Explicitní načítání objektů vyžaduje odezvu do `Load` databáze pokaždé, když je volána.  
  
> [!NOTE]
> Pokud voláte `Load` při opakování prostřednictvím kolekce vrácených objektů, `foreach` například při použití příkazu (v`For Each` jazyce Visual Basic), zprostředkovatel specifické pro zdroj dat musí podporovat více sad aktivních výsledků na jedno připojení. Pro databázi serveru SQL Server je `MultipleActiveResultSets = true` nutné zadat hodnotu v připojovacím řetězci zprostředkovatele.  
  
 Metodu můžete <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> také použít, <xref:System.Data.Objects.DataClasses.EntityCollection%601> pokud <xref:System.Data.Objects.DataClasses.EntityReference%601> na entitách nejsou žádné nebo vlastnosti. To je užitečné, pokud používáte entity POCO.  
  
 Přestože explicitně načítání souvisejících objektů sníží počet spojení a `Load` sníží množství redundantních dat, vyžaduje opakované připojení k databázi, což může být nákladné při explicitním načítání velkého počtu objektů.  
  
### <a name="saving-changes"></a>Ukládání změn  
 Při volání <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metody v <xref:System.Data.Objects.ObjectContext>aplikaci je pro každý přidaný, aktualizovaný nebo odstraněný objekt v kontextu generován samostatný příkaz create, update nebo delete. Tyto příkazy jsou spouštěny na zdroj dat v jedné transakci. Stejně jako u dotazů závisí výkon operací vytváření, aktualizace a odstranění na složitosti mapování v koncepčním modelu.  
  
### <a name="distributed-transactions"></a>Distribuované transakce  
 Operace v explicitní transakce, které vyžadují prostředky, které jsou spravovány koordinátorem distribuovaných transakcí (DTC) bude mnohem dražší než podobné operace, která nevyžaduje Koordinátor DTC. Povýšení na DTC dojde v následujících situacích:  
  
- Explicitní transakce s operací proti databázi SERVERU SQL Server 2000 nebo jinému zdroji dat, které vždy podporují explicitní transakce do koordinátoru DTC.  
  
- Explicitní transakce s operací proti serveru SQL Server 2005 při spravování připojení rozhraním entity Framework. K tomu dochází, protože SQL Server 2005 povýší na dtc vždy, když je připojení uzavřeno a znovu otevřeno v rámci jedné transakce, což je výchozí chování entity framework. Tato podpora dtc nedochází při použití SQL Server 2008. Chcete-li se vyhnout této podpoře při použití serveru SQL Server 2005, je nutné explicitně otevřít a zavřít připojení v rámci transakce. Další informace naleznete v [tématu Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
 Explicitní transakce se používá, když jedna nebo <xref:System.Transactions> více operací jsou prováděny uvnitř transakce. Další informace naleznete v [tématu Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="strategies-for-improving-performance"></a>Strategie pro zlepšení výkonnosti  
 Můžete zlepšit celkový výkon dotazů v entity framework pomocí následujících strategií.  
  
#### <a name="pre-generate-views"></a>Předgenerování zobrazení  
 Generování pohledů založených na modelu entity je značné náklady při prvním spuštění dotazu aplikací. Pomocí nástroje EdmGen.exe předem vygenerujte zobrazení jako soubor kódu jazyka Visual Basic nebo C#, který lze přidat do projektu během návrhu. Můžete také použít sadu nástrojů transformace šablony textu ke generování předem zkompilovaných zobrazení. Předem vygenerovaná zobrazení jsou ověřena za běhu, aby bylo zajištěno, že jsou konzistentní s aktuální verzí zadaného modelu entity. Další informace naleznete v [tématu How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).
  
 Při práci s velmi velkými modely platí následující pozornost:  
  
 Formát metadat .NET omezuje počet znaků uživatelského řetězce v daném binárním souboru na 16 777 215 (0xFFFFFF). Pokud generujete pohledy pro velmi velký model a soubor zobrazení dosáhne tohoto limitu velikosti, získáte "Nezbývá žádné logické místo pro vytvoření více uživatelských řetězců." chyba kompilace. Toto omezení velikosti platí pro všechny spravované binární soubory. Další informace naleznete v [blogu,](https://docs.microsoft.com/archive/blogs/appfabriccat/solving-the-no-logical-space-left-to-create-more-user-strings-error-and-improving-performance-of-pre-generated-views-in-visual-studio-net4-entity-framework) který ukazuje, jak se vyhnout chybě při práci s velkými a složitými modely.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Zvažte použití možnosti sloučení NoTracking pro dotazy  
 Je nutné sledovat vrácené objekty v kontextu objektu. Zjištění změn objektů a zajištění, že více požadavků na stejnou logickou entitu vrátí <xref:System.Data.Objects.ObjectContext> stejnou instanci objektu, vyžaduje, aby byly objekty připojeny k instanci. Pokud neplánujete provádět aktualizace nebo odstraňuje na objekty a nevyžadují <xref:System.Data.Objects.MergeOption.NoTracking> správu identit, zvažte použití možností sloučení při provádění dotazů.  
  
#### <a name="return-the-correct-amount-of-data"></a>Vrátit správné množství dat  
 V některých případech je určení <xref:System.Data.Objects.ObjectQuery%601.Include%2A> cesty dotazu pomocí metody mnohem rychlejší, protože vyžaduje méně zpátečních cest do databáze. V jiných scénářích však další zpáteční cesty do databáze načíst související objekty může být rychlejší, protože jednodušší dotazy s menším počtem spojení za následek menší redundanci dat. Z tohoto důvodu doporučujeme otestovat výkon různých způsobů načtení souvisejících objektů. Další informace naleznete v [tématu Načítání souvisejících objektů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
 Chcete-li se vyhnout vrácení příliš mnoho dat v jednom dotazu, zvažte stránkování výsledky dotazu do více spravovatelné skupiny. Další informace naleznete v [tématu How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>Omezit rozsah ObjectContext  
 Ve většině případů byste <xref:System.Data.Objects.ObjectContext> měli vytvořit `using` instanci v rámci příkazu (v`Using…End Using` jazyce Visual Basic). To může zvýšit výkon tím, že zajistí, že prostředky spojené s kontextem objektu jsou uvolněny automaticky, když kód ukončí blok příkazu. Však při ovládací prvky jsou vázány <xref:System.Data.Objects.ObjectContext> na objekty spravované kontextu objektu, instance by měla být zachována tak dlouho, dokud je potřeba vazby a uvolněna ručně. Další informace naleznete v [tématu Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Zvažte ruční otevření připojení k databázi.  
 Když vaše aplikace spustí řadu dotazů na <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> objekty nebo často volá zachovat vytvořit, aktualizovat a odstranit operace ke zdroji dat, entity framework musí neustále otevřít a zavřít připojení ke zdroji dat. V těchto situacích zvažte ruční otevření připojení na začátku těchto operací a zavření nebo likvidaci připojení po dokončení operací. Další informace naleznete v [tématu Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="performance-data"></a>Data výkonu  
 Některá data o výkonu pro entity framework je zveřejněna v následujících příspěvcích na [blogu týmu ADO.NET](https://docs.microsoft.com/archive/blogs/adonet/):  
  
- [Zkoumání výkonnosti rámce ADO.NET subjektů – část 1](https://docs.microsoft.com/archive/blogs/adonet/exploring-the-performance-of-the-ado-net-entity-framework-part-1)  
  
- [Zkoumání výkonnosti rámce ADO.NET subjektů – část 2](https://docs.microsoft.com/archive/blogs/adonet/exploring-the-performance-of-the-ado-net-entity-framework-part-2)  
  
- [Porovnání výkonnosti rámce entity ADO.NET](https://docs.microsoft.com/archive/blogs/adonet/ado-net-entity-framework-performance-comparison)  
  
## <a name="see-also"></a>Viz také

- [Důležité informace o vývoji a nasazení](development-and-deployment-considerations.md)
