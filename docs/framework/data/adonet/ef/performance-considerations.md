---
title: "Faktory ovlivňující výkon (rozhraní Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dd42175234418ebd260a85c87bfeae6cf59ceb4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="performance-considerations-entity-framework"></a>Faktory ovlivňující výkon (rozhraní Entity Framework)
Toto téma popisuje výkonové charakteristiky ADO.NET Entity Framework a poskytuje některé aspekty určené k pomoct zlepšit výkon aplikací rozhraní Entity Framework.  
  
## <a name="stages-of-query-execution"></a>Fáze spuštění dotazu  
 Aby bylo možné lépe pochopit výkon dotazů v rozhraní Entity Framework, je vhodné se seznámit s operací, které dojít, když dotaz provede pro koncepční model a vrátí data jako objekty. Následující tabulka popisuje tuto řadu operace.  
  
|Operace|Relativní náklady|frekvence|Komentáře|  
|---------------|-------------------|---------------|--------------|  
|Načítání metadat|Střední|Jednou v každé doméně aplikace.|Mapování a modelu metadat používá rozhraní Entity Framework je načten do <xref:System.Data.Metadata.Edm.MetadataWorkspace>. Tato metadata do globální mezipaměti a je k dispozici pro ostatní instance <xref:System.Data.Objects.ObjectContext> ve stejné doméně aplikace.|  
|Otevření připojení k databázi|Střední<sup>1</sup>|podle potřeby.|Protože otevřené připojení k databázi spotřebovává cenné prostředku, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] otevře a uzavře připojení k databázi, podle potřeby. Můžete také explicitně otevřít připojení. Další informace najdete v tématu [Správa připojení a transakce](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).|  
|Generování zobrazení|Vysoká|Jednou v každé doméně aplikace. (Může být předem vygenerovaná.)|Než rozhraní Entity Framework můžete zadávat dotazy na koncepční model, nebo uložit změny pro zdroj dat, musíte vygenerovat sadu zobrazení místní dotazu pro přístup k databázi. Z důvodu vysoké náklady na generování tato zobrazení můžete předběžnému generování zobrazení a přidat je do tohoto projektu v době návrhu. Další informace najdete v tématu [postupy: zobrazení Pre-Generate ke zlepšení výkonu dotazů](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579).|  
|Příprava dotazu|Střední<sup>2</sup>|Jednou pro každý jedinečný dotaz.|Zahrnuje náklady na napište příkaz dotazu, generovat stromu příkazů na základě modelu a mapování metadat a definovat obrazec vrácená data. Protože teď Entity SQL dotazu příkazů a dotazů LINQ jsou uložené v mezipaměti, novější spuštěních stejný dotaz trvat méně času. Můžete nadále používat kompilované dotazů LINQ na snížení nákladů na tento v novější spuštěních a kompilované dotazy může být efektivnější než LINQ dotazů, které jsou automaticky uloží do mezipaměti. Další informace najdete v tématu [zkompilovat dotazy (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md). Obecné informace o spuštění dotazu LINQ najdete v tématu [technologie LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md). **Poznámka:** technologie LINQ to Entities dotazy, které se vztahují `Enumerable.Contains` operátor do kolekcí v paměti neukládají do mezipaměti automaticky. Také Parametrizace kolekce v paměti v kompilovaném dotazů LINQ není povoleno.|  
|Provádění dotazu|Nízká<sup>2</sup>|Jednou pro každý dotaz.|Náklady na provádění příkazu na zdroji dat pomocí zprostředkovatele dat ADO.NET. Protože většina zdroje dat do mezipaměti plány dotazů, novější spuštěních stejný dotaz může trvat i méně času.|  
|Načítání a ověřování typů|Nízká<sup>3</sup>|Jednou pro každou <xref:System.Data.Objects.ObjectContext> instance.|Typy jsou načteny a ověřovat s typy, které definuje konceptuálního modelu.|  
|Sledování|Nízká<sup>3</sup>|Jednou pro každý objekt, který vrací dotaz. <sup>4</sup>|Pokud dotaz používá <xref:System.Data.Objects.MergeOption.NoTracking> možnosti sloučení, tato fáze nemá vliv na výkon.<br /><br /> Pokud dotaz používá <xref:System.Data.Objects.MergeOption.AppendOnly>, <xref:System.Data.Objects.MergeOption.PreserveChanges>, nebo <xref:System.Data.Objects.MergeOption.OverwriteChanges> merge – možnost, výsledky jsou sledovány v dotazu <xref:System.Data.Objects.ObjectStateManager>. <xref:System.Data.EntityKey> Se vygeneruje pro každý sledovaný objekt, který dotaz vrátí, je použít k vytvoření <xref:System.Data.Objects.ObjectStateEntry> v <xref:System.Data.Objects.ObjectStateManager>. Pokud existující <xref:System.Data.Objects.ObjectStateEntry> pro nebyl nalezen <xref:System.Data.EntityKey>, je vrácen existující objekt. Pokud <xref:System.Data.Objects.MergeOption.PreserveChanges>, nebo <xref:System.Data.Objects.MergeOption.OverwriteChanges> možnost se používá, aktualizaci objektu před vrácením.<br /><br /> Další informace najdete v tématu [řešení Identity, řízení stavu a sledování změn](http://msdn.microsoft.com/en-us/3bd49311-0e72-4ea4-8355-38fe57036ba0).|  
|Vyhodnocování objekty|Střední<sup>3</sup>|Jednou pro každý objekt, který vrací dotaz. <sup>4</sup>|Proces načítání vrácený <xref:System.Data.Common.DbDataReader> objekt a vytváření objektů a nastavení hodnoty vlastností, které jsou na základě hodnot v každé instanci <xref:System.Data.Common.DbDataRecord> třídy. Pokud objekt již existuje v <xref:System.Data.Objects.ObjectContext> a použije dotaz <xref:System.Data.Objects.MergeOption.AppendOnly> nebo <xref:System.Data.Objects.MergeOption.PreserveChanges> možností sloučení, tato fáze nemá vliv na výkon. Další informace najdete v tématu [řešení Identity, řízení stavu a sledování změn](http://msdn.microsoft.com/en-us/3bd49311-0e72-4ea4-8355-38fe57036ba0).|  
  
 <sup>1</sup> při Zprostředkovatel zdroje dat implementuje sdružování připojení, náklady na otevření připojení je distribuován do fondu. Zprostředkovatel rozhraní .NET pro SQL Server podporuje sdružování připojení.  
  
 <sup>2</sup> náklady se zvyšuje s vyšší dotazu složitost.  
  
 <sup>3</sup> zvýšení celkové náklady na úměrná počet objektů vrácených dotazem.  
  
 <sup>4</sup> režijní náklady na tento není požadovaná pro EntityClient dotazy, protože zprostředkovatel EntityClient dotazuje vrátit <xref:System.Data.EntityClient.EntityDataReader> místo objekty. Další informace najdete v tématu [zprostředkovatel EntityClient rozhraní Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Další informace  
 Zde jsou další důležité informace, které může mít vliv na výkon aplikací rozhraní Entity Framework.  
  
### <a name="query-execution"></a>Provádění dotazů  
 Protože dotazy může být náročné, zvažte, jaký okamžiku ve vašem kódu a v počítači, jaké je dotaz proveden.  
  
#### <a name="deferred-versus-immediate-execution"></a>Odložení versus okamžité spuštění  
 Při vytváření <xref:System.Data.Objects.ObjectQuery%601> nebo dotaz LINQ, nemusí být okamžitě spustit dotaz. Při provádění dotazu je odložení, dokud jsou potřeba výsledky, například během `foreach` (C#) nebo `For Each` – výčet (Visual Basic) nebo pokud je přiřazená k vyplnění <xref:System.Collections.Generic.List%601> kolekce. Při provádění dotazu začne okamžitě při volání <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> metodu <xref:System.Data.Objects.ObjectQuery%601> nebo při volání metody LINQ dotazů s jediným prvkem vrátí například <xref:System.Linq.Enumerable.First%2A> nebo <xref:System.Linq.Enumerable.Any%2A>. Další informace najdete v tématu [objekt dotazy](http://msdn.microsoft.com/en-us/0768033c-876f-471d-85d5-264884349276) a [provádění dotazu (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>Klientské provádění dotazů LINQ  
 I když dojde k provedení dotazu LINQ na počítači, který je hostitelem zdroje dat, některé části dotazu LINQ může vyhodnotí v klientském počítači. Další informace najdete v části úložiště provádění z [provádění dotazu (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
### <a name="query-and-mapping-complexity"></a>Dotaz a mapování složitost  
 Složitost jednotlivých dotazů a mapování v modelu entity bude mít významný vliv na výkon dotazů.  
  
#### <a name="mapping-complexity"></a>Mapování složitost  
 Modely, které jsou složitější než jednoduché mapování 1: 1 mezi entity v konceptuálním modelu a tabulek v rámci modelu úložiště vygenerovat složitější příkazy než modely, které mají mapování 1: 1.  
  
#### <a name="query-complexity"></a>Složitost dotazu  
 Dotazy, které vyžadují velký počet spojení v příkazech, které jsou spouštěny na zdroji dat nebo velké množství dat, které vracejí mohou ovlivnit výkon následujícími způsoby:  
  
-   Dotazy na pro konceptuální model i zdánlivě může vést k provádění složitějších dotazů na zdroji dat. Tato situace může nastat, protože rozhraní Entity Framework překládá do ekvivalentní dotaz zdroje dat dotazu vůči konceptuálního modelu. Při nastavení jedna entita v konceptuálním modelu se mapuje na více než jedné tabulky ve zdroji dat nebo když vztahu mezi entitami se mapuje na tabulku spojení, příkaz dotaz spustit pro dotaz na datový zdroj můžou vyžadovat jeden nebo více spojení.  
  
    > [!NOTE]
    >  Použití <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metodu <xref:System.Data.Objects.ObjectQuery%601> nebo <xref:System.Data.EntityClient.EntityCommand> třídy zobrazíte příkazy, které jsou spouštěny na zdroji dat pro daný dotaz. Další informace najdete v tématu [postupy: zobrazení příkazy úložiště](http://msdn.microsoft.com/en-us/f9771c6e-3b62-4b24-a5d4-55d68e14fa79).  
  
-   Vnořené dotazy na Entity SQL na serveru může vytvořit spojení a může vrátit velký počet řádků.  
  
     Následuje příklad vnořený dotaz v klauzuli projekce:  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Kromě toho takové dotazy způsobit dotazu kanál ke generování jeden dotaz s duplicitních objektů mezi vnořené dotazy. Z toho důvodu může být jeden sloupec duplicitní vícekrát. Na některé databáze, včetně systému SQL Server to může způsobit tabulky databáze TempDB růst velký, který může snížit výkon serveru. Potřeba dát pozor při spuštění vnořené dotazy.  
  
-   Všechny dotazy, které mají být návratové že velké množství dat může způsobit snížení výkonu, pokud klient provádí operace, které mohly spotřebovávat prostředky způsobem, který je přímo úměrná velikosti sady výsledků dotazu. V takových případech zvažte omezení množství dat vrácených dotazem. Další informace najdete v tématu [postup: stránku prostřednictvím výsledky dotazu](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030).  
  
 Všechny příkazy, které automaticky generuje služba rozhraní Entity Framework může být složitější než podobné příkazy, které jsou napsané explicitně vývojáři databáze. Pokud potřebujete explicitní kontrolu nad příkazy spustit pro zdroj dat, zvažte, definování mapování funkce vracející tabulku nebo uložené procedury.  
  
#### <a name="relationships"></a>Relace  
 Pro dotaz optimální výkon je nutné definovat vztahy mezi entitami jako atributy Association v modelu entity i jako logické vztahy v datovém zdroji.  
  
### <a name="query-paths"></a>Dotaz cesty  
 Ve výchozím nastavení při spuštění <xref:System.Data.Objects.ObjectQuery%601>, související objekty nebudou zobrazeny (i když jsou objekty, které představují samotné vztahy). Je možné načíst objekty v relaci v jednom ze tří způsobů:  
  
1.  Nastavení cesty dotazu před <xref:System.Data.Objects.ObjectQuery%601> se spustí.  
  
2.  Volání `Load` metodu na navigační vlastnost, která zveřejňuje objektu.  
  
3.  Nastavte <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> možnost <xref:System.Data.Objects.ObjectContext> k `true`. Všimněte si, že to se provádí automaticky při generování kódu objektové vrstvě pomocí [Entity Data Model Designer](http://msdn.microsoft.com/en-us/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf). Další informace najdete v části [vygeneruje kód přehled](http://msdn.microsoft.com/en-us/6a88ea38-6a90-4107-bc33-531b79ce5b6a).  
  
 Pokud uvažujete o možnost provedení, mějte na paměti, že je kompromis mezi počet požadavků v databázi a množství dat, vrátí se v jednom dotazu. Další informace najdete v tématu [načítání související objekty](http://msdn.microsoft.com/en-us/452347d2-7b3b-44cd-9001-231299a28cb1).  
  
#### <a name="using-query-paths"></a>Pomocí dotazu cesty  
 Cesty dotazu definovat grafu objektů, které vrací dotaz. Když definujete cestu dotazu, je potřeba pouze jeden požadavek proti dané databázi vrátit všechny objekty, které definuje cestu. Pomocí dotazu cesty, může mít za následek komplexní příkazy, které se spouštějí na zdroji dat z zdánlivě jednoduchého objektu dotazů. K tomu dochází, protože jeden nebo více spojení jsou nutné k vrácení souvisejících objektů, které v jednom dotazu. Tato složitost je větší v dotazy pro komplexní entity modelu, například entity s dědičnosti nebo cestu, která obsahuje relace m: n.  
  
> [!NOTE]
>  Použití <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metoda zobrazíte příkaz, který vygeneruje <xref:System.Data.Objects.ObjectQuery%601>. Další informace najdete v tématu [postupy: zobrazení příkazy úložiště](http://msdn.microsoft.com/en-us/f9771c6e-3b62-4b24-a5d4-55d68e14fa79).  
  
 Pokud cestu dotazu obsahuje příliš mnoho související objekty nebo objekty obsahovat příliš mnoho řádek dat, může být zdroje dat nelze dokončit dotaz. K tomu dojde, pokud vyžaduje zprostředkující dočasné úložiště, která překračuje možnosti zdroje dat dotazu. V takovém případě můžete snížit složitost dotazu na datový zdroj explicitně načtením související objekty.  
  
#### <a name="explicitly-loading-related-objects"></a>Explicitně načítání související objekty  
 Souvisejících objektů, které můžete načíst explicitně voláním `Load` metoda na navigační vlastnost, která vrátí <xref:System.Data.Objects.DataClasses.EntityCollection%601> nebo <xref:System.Data.Objects.DataClasses.EntityReference%601>. Explicitně načítání objektů round-trip do databáze vyžaduje pokaždé, když `Load` je volána.  
  
> [!NOTE]
>  Při volání `Load` při ve smyčce přes kolekce vrácených objektů, například při použití `foreach` – příkaz (`For Each` v jazyce Visual Basic), poskytovatel specifická pro zdroj dat musí podporovat více sad výsledků active na jednom připojení. Pro databázi systému SQL Server, musíte zadat hodnotu `MultipleActiveResultSets = true` v připojovacím řetězci zprostředkovatele.  
  
 Můžete také <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> metoda při žádné <xref:System.Data.Objects.DataClasses.EntityCollection%601> nebo <xref:System.Data.Objects.DataClasses.EntityReference%601> vlastnosti entity. To je užitečné, když používáte entity objektů POCO.  
  
 I když explicitně načítání související objekty se sníží počet spojení a snížit množství redundantních dat `Load` vyžaduje opakované připojení k databázi, která se může stát nákladná při explicitně načítání velkého počtu objektů.  
  
### <a name="saving-changes"></a>Ukládají se změny  
 Při volání <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metodu <xref:System.Data.Objects.ObjectContext>, samostatné vytvoření, aktualizace a odstranění příkaz se vygeneruje pro každý objekt přidaný, aktualizovaných nebo odstraněných v kontextu. Tyto příkazy jsou provedeny ve zdroji dat v rámci jedné transakce. S dotazy, výkon vytvořit, aktualizovat a odstranit operace závisí na složitosti mapování v konceptuálním modelu.  
  
### <a name="distributed-transactions"></a>Distribuované transakce  
 Operace v explicitní transakce, které vyžadují prostředky, které jsou spravovány koordinátor distribuovaných transakcí (DTC) bude výrazně dražší než podobná operace, která nevyžaduje službu. Povýšení na službu dojde v následujících situacích:  
  
-   Explicitní transakce s operace proti databáze systému SQL Server 2000 nebo jiné zdroje dat, která vždy zvýšit úroveň explicitní transakcí koordinátoru DTC.  
  
-   Explicitní transakce s operací pro SQL Server 2005, když je připojení spravuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. K tomu dochází, protože systém SQL Server 2005 zvýší úroveň na DTC vždy, když je připojení zavřít a znovu otevřít v rámci jedné transakce, což je výchozí chování [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Tato služba DTC povýšení neproběhne při použití systému SQL Server 2008. Abyste předešli této povýšení při použití systému SQL Server 2005, musí explicitně otevírají a zavírají připojení v rámci transakce. Další informace najdete v tématu [Správa připojení a transakce](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
 Explicitní transakce se používá při provedení jednu nebo více operací uvnitř <xref:System.Transactions> transakce. Další informace najdete v tématu [Správa připojení a transakce](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="strategies-for-improving-performance"></a>Strategie pro zvýšení výkonu  
 Pomocí následujících strategií může zvýšit celkový výkon dotazů v Entity Framework.  
  
#### <a name="pre-generate-views"></a>Předběžnému generování zobrazení  
 Generování zobrazení založená na modelu entity je poprvé, že aplikace provede dotaz výrazné náklady. Použijte nástroj EdmGen.exe k předběžnému generování zobrazení v souboru kódu Visual Basic a C#, který lze přidat do projektu při návrhu. Můžete použít taky Toolkit Text šablony transformace pro generování předem kompilovaném zobrazení. Předem vygenerovaných zobrazení se ověřují v době běhu k zajištění, že jsou konzistentní s aktuální verze modelu zadané entity. Další informace najdete v tématu [postupy: zobrazení Pre-Generate ke zlepšení výkonu dotazů](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579) a [izolace výkonu předkompilované nebo vedlejší-generated zobrazení v rozhraní Entity Framework 4](http://go.microsoft.com/fwlink/?LinkID=201337&clcid=0x409).  
  
 Při práci s velmi velké modely, platí následující úvahy:  
  
 Formát metadata rozhraní .NET omezuje počet znaků řetězce uživatele v dané binární na 16 777 215 (0xFFFFFF). Pokud jsou generování zobrazení pro model velmi velké a zobrazit soubor dosáhne tento limit pro velikost, zobrazí se "již není logické místo vytvořit další uživatele řetězce." Chyba kompilace. Toto omezení velikosti platí pro všechny spravované binární soubory. Další informace najdete v článku [blog](http://go.microsoft.com/fwlink/?LinkId=201476) který ukazuje, jak nedošlo k chybě při práci s modely, velký a složitější.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Vezměte v úvahu pomocí možnosti sloučení NoTracking pro dotazy  
 Není k dispozici s náklady nezbytné ke sledování vrácených objektů v kontextu objektu. Detekovat změny objektů a zajistíte, že více požadavků pro stejnou logická entita vrátit stejnou instanci objektu vyžaduje, aby objekty být připojen k <xref:System.Data.Objects.ObjectContext> instance. Pokud nemáte v plánu provést aktualizace nebo odstranění na objekty a nevyžadují správu identit, zvažte použití <xref:System.Data.Objects.MergeOption.NoTracking> možnosti sloučení, při spuštění dotazů.  
  
#### <a name="return-the-correct-amount-of-data"></a>Vrátí správné množství dat  
 V některých scénářích zadání cesty dotaz pomocí <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metoda je mnohem rychlejší, protože vyžaduje menší počet zpátečních cest k databázi. Ale v jiných scénářích další zpátečních cest k databázi a načítání souvisejících objektů, které může být rychlejší protože jednodušší dotazy s méně spojení mít za následek menší redundanci dat. Z toho důvodu doporučujeme, že provedete test výkonu různých způsobů, jak načíst objekty v relaci. Další informace najdete v tématu [načítání související objekty](http://msdn.microsoft.com/en-us/452347d2-7b3b-44cd-9001-231299a28cb1).  
  
 Abyste se vyhnuli, vrácení příliš mnoho dat v jednom dotazu, vezměte v úvahu stránkování výsledků dotazu do udržitelnější skupin. Další informace najdete v tématu [postup: stránku prostřednictvím výsledky dotazu](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030).  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>Omezit rozsah ObjectContext  
 Ve většině případů byste měli vytvořit <xref:System.Data.Objects.ObjectContext> instance v rámci `using` – příkaz (`Using…End Using` v jazyce Visual Basic). To může zvýšit výkon zajištěním prostředky přidružené k objektu kontextu jsou při kód ukončení bloku příkaz zlikvidován automaticky. Ale když vazby ovládacích prvků na objekty, které spravuje kontext objektu <xref:System.Data.Objects.ObjectContext> instance by se měl zachovat, dokud, vazba je potřeba a ručně odstraněny. Další informace najdete v tématu [Správa připojení a transakce](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Vezměte v úvahu otevření připojení k databázi ručně  
 Pokud aplikace provede řadu objekt dotazy nebo často volá <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> udržení vytvářet, aktualizovat a odstraňovat operations ke zdroji dat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] musí nepřetržitě otevírají a zavírají připojení ke zdroji dat. V těchto situacích zvažte ručně otevření připojení na začátku těchto operací a zavírání nebo uvolnění připojení po dokončení operace. Další informace najdete v tématu [Správa připojení a transakce](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="performance-data"></a>Údaje o výkonu  
 Některé údaje o výkonu pro rozhraní Entity Framework je publikována v následujících příspěvcích na [blog týmu ADO.NET](http://go.microsoft.com/fwlink/?LinkId=91905):  
  
-   [Zkoumání výkonu technologie ADO.NET Entity Framework – část 1](http://go.microsoft.com/fwlink/?LinkId=123907)  
  
-   [Zkoumání výkonu technologie ADO.NET Entity Framework – část 2](http://go.microsoft.com/fwlink/?LinkId=123909)  
  
-   [Porovnání výkonu technologie ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>Viz také  
 [Vývoj a aspekty nasazení](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
