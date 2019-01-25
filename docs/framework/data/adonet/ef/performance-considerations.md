---
title: Důležité informace o výkonu (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: 43194baeaaeefd8748980a8542bea199d3e8d29f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732008"
---
# <a name="performance-considerations-entity-framework"></a>Důležité informace o výkonu (Entity Framework)
Toto téma popisuje charakteristiky výkonu technologie ADO.NET Entity Framework a obsahuje některé aspekty, které pomůžou zlepšit výkon aplikací využívajících rozhraní Entity Framework.  
  
## <a name="stages-of-query-execution"></a>Fáze spuštění dotazu  
 Chcete-li lépe pochopit výkon dotazů v Entity Framework, je dobré znát operace, které nastaly, když dotaz provede pro koncepční model a vrátí dat jako objektů. Následující tabulka popisuje tato posloupnost operací.  
  
|Operace|Relativní náklady|Frekvence|Komentáře|  
|---------------|-------------------|---------------|--------------|  
|Načítání metadat|Střední|Jednou v každé doméně aplikace.|Metadata modelu a mapování používaná rozhraním Entity Framework je načten do <xref:System.Data.Metadata.Edm.MetadataWorkspace>. Tato metadata je globálně do mezipaměti a je k dispozici pro ostatní instance <xref:System.Data.Objects.ObjectContext> ve stejné doméně aplikace.|  
|Otevření připojení k databázi|Střední<sup>1</sup>|Podle potřeby.|Protože otevřeného připojení k databázi spotřebovává cenné prostředků [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] otevře a uzavře připojení k databázi podle potřeby. Můžete také explicitně otevřít připojení. Další informace najdete v tématu [Správa připojení a transakce](https://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).|  
|Generování zobrazení|Vysoká|Jednou v každé doméně aplikace. (Může být předem generovaného.)|Entity Framework mohli spustit dotaz pro koncepční model nebo uložit změny do zdroje dat, musíte vygenerovat sadu zobrazení místní dotazu pro přístup k databázi. Z důvodu vysoké náklady na generování těchto zobrazení můžete předem vygenerovat zobrazení a přidat je do projektu v době návrhu. Další informace najdete v tématu [jak: Předběžně generovat zobrazení pro zlepšení výkonu dotazů](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579).|  
|Příprava dotazu|Střední<sup>2</sup>|Jednou pro každý dotaz jedinečný.|Zahrnují náklady na vytvoření příkazu dotazu, generovat stromu příkazů na základě modelu a mapování metadata a definovat tvar vrácená data. Protože teď Entity SQL dotazu příkazů a dotazů LINQ jsou ukládány do mezipaměti, vyšší počet spuštění stejného dotazu trvat kratší dobu. Stále vám pomůže kompilované dotazy LINQ v pozdější spuštění tyto náklady snížit a kompilované dotazy může být efektivnější než LINQ dotazy, které se automaticky uloží do mezipaměti. Další informace najdete v tématu [zkompilován dotazy (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md). Obecné informace o provádění dotazů LINQ, naleznete v tématu [technologii LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md). **Poznámka:**  Dotazech LINQ to Entities, které se vztahují `Enumerable.Contains` nejsou v operátoru na kolekce v paměti automaticky uložené v mezipaměti. Také Parametrizace kolekce v paměti v kompilované dotazy LINQ není povoleno.|  
|Provádění dotazu|Nízká<sup>2</sup>|Jednou pro každý dotaz.|Náklady na provedení příkazu na zdroji dat pomocí zprostředkovatele dat ADO.NET. Protože většina zdrojů dat do mezipaměti plány dotazů, novější spuštění stejný dotaz může trvat i méně času.|  
|Načítání a ověření typů|Nízká<sup>3</sup>|Jednou pro každé <xref:System.Data.Objects.ObjectContext> instance.|Typy jsou načten a ověřen typy, které definuje konceptuálního modelu.|  
|Sledování|Nízká<sup>3</sup>|Jednou pro každý objekt, který dotaz vrátí. <sup>4</sup>|Pokud se používá dotaz <xref:System.Data.Objects.MergeOption.NoTracking> možnost sloučení, tuto fázi nemá vliv na výkon.<br /><br /> Pokud dotaz používá <xref:System.Data.Objects.MergeOption.AppendOnly>, <xref:System.Data.Objects.MergeOption.PreserveChanges>, nebo <xref:System.Data.Objects.MergeOption.OverwriteChanges> merge – možnost, výsledky jsou sledovány v dotazu <xref:System.Data.Objects.ObjectStateManager>. <xref:System.Data.EntityKey> Je vygenerována pro každý dotaz vrací a je sledované objekt použitý k vytvoření <xref:System.Data.Objects.ObjectStateEntry> v <xref:System.Data.Objects.ObjectStateManager>. Existující <xref:System.Data.Objects.ObjectStateEntry> nebyla nalezena <xref:System.Data.EntityKey>, stávající objekt je vrácen. Pokud <xref:System.Data.Objects.MergeOption.PreserveChanges>, nebo <xref:System.Data.Objects.MergeOption.OverwriteChanges> možnost se používá, je objekt aktualizován před vrácením.<br /><br /> Další informace najdete v tématu [rozlišení Identity, správy stavu a Change Tracking](https://msdn.microsoft.com/library/3bd49311-0e72-4ea4-8355-38fe57036ba0).|  
|Materializaci objekty|Střední<sup>3</sup>|Jednou pro každý objekt, který dotaz vrátí. <sup>4</sup>|Proces čtení vráceného <xref:System.Data.Common.DbDataReader> objektu a vytváření objektů a nastavení hodnoty vlastností, které jsou založené na hodnotách v každé instanci <xref:System.Data.Common.DbDataRecord> třídy. Pokud objekt již existuje v <xref:System.Data.Objects.ObjectContext> a použije dotaz <xref:System.Data.Objects.MergeOption.AppendOnly> nebo <xref:System.Data.Objects.MergeOption.PreserveChanges> možností sloučení, tuto fázi nemá vliv na výkon. Další informace najdete v tématu [rozlišení Identity, správy stavu a Change Tracking](https://msdn.microsoft.com/library/3bd49311-0e72-4ea4-8355-38fe57036ba0).|  
  
 <sup>1</sup> při Zprostředkovatel zdroje dat implementuje sdružování připojení, náklady na otevření připojení se distribuuje do fondu. Zprostředkovatel rozhraní .NET pro SQL Server podporuje sdružování připojení.  
  
 <sup>2</sup> náklady se zvyšuje s dotazu zvýšení složitosti.  
  
 <sup>3</sup> zvýšení celkové náklady na úměrný počtu objektů vrácených dotazem.  
  
 <sup>4</sup> tato režie se nevyžaduje, pro zprostředkovatel EntityClient dotazuje, protože zprostředkovatel EntityClient dotazuje vrátit <xref:System.Data.EntityClient.EntityDataReader> místo objekty. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Další informace  
 Tady jsou další důležité informace, které mohou ovlivňovat výkon aplikace Entity Framework.  
  
### <a name="query-execution"></a>Provádění dotazů  
 Vzhledem k tomu, že dotazy může být náročné, zvažte, na kterém bodě v kódu a na jaké počítače je dotaz proveden.  
  
#### <a name="deferred-versus-immediate-execution"></a>Odložené versus okamžité spuštění  
 Při vytváření <xref:System.Data.Objects.ObjectQuery%601> nebo dotazu LINQ dotaz nemusí být provedena okamžitě. Provádění dotazu je odloženo, dokud jsou potřebné výsledky, jako například během `foreach` (C#) nebo `For Each` výčtu (Visual Basic) nebo když je přiřazený k vyplnění <xref:System.Collections.Generic.List%601> kolekce. Provádění dotazů začne okamžitě při volání <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> metodu <xref:System.Data.Objects.ObjectQuery%601> nebo při volání metody LINQ vrátí dotazů s jediným prvkem, jako například <xref:System.Linq.Enumerable.First%2A> nebo <xref:System.Linq.Enumerable.Any%2A>. Další informace najdete v tématu [dotazy objektu](https://msdn.microsoft.com/library/0768033c-876f-471d-85d5-264884349276) a [provádění dotazů (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>Na straně klienta provádění dotazů LINQ  
 I když dojde k provádění dotazů LINQ v počítači, který je hostitelem zdroje dat, může být vyhodnocen některé části dotazu LINQ na klientském počítači. Další informace najdete v části spuštění Store v [provádění dotazů (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
### <a name="query-and-mapping-complexity"></a>Dotaz a mapování složitost  
 Složitost jednotlivých dotazů a mapování v modelu entity budou mít významný vliv na výkon dotazů.  
  
#### <a name="mapping-complexity"></a>Mapování složitost  
 Modely, které jsou složitější než jednoduché mapování 1: 1 mezi entitami v konceptuálním modelu a tabulky v modelu úložiště vygenerovat složitější příkazy než modely, které mají mapování 1: 1.  
  
#### <a name="query-complexity"></a>Složitosti dotazu  
 Dotazy, které vyžadují velký počet spojení v příkazech, které jsou spouštěny na zdroji dat nebo, které vracejí velké množství dat může ovlivnit výkon následujícími způsoby:  
  
-   Dotazy na konceptuální model, které vypadá to, že jednoduchá může vést k provádění na zdroji dat složitější dotazy. Tato situace může nastat, protože rozhraní Entity Framework překládá na ekvivalentní dotazu na zdroji dat dotazu na koncepční model. Při nastavení jedné entity v konceptuálním modelu mapuje na více než jedné tabulky ve zdroji dat nebo když relace mezi entitami se mapuje na tabulku spojení, příkaz dotazu pro dotaz na zdroj dat může vyžadovat jeden nebo více spojení.  
  
    > [!NOTE]
    >  Použití <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metodu <xref:System.Data.Objects.ObjectQuery%601> nebo <xref:System.Data.EntityClient.EntityCommand> třídy zobrazit příkazy, které jsou prováděny nad zdrojem dat pro daný dotaz. Další informace najdete v tématu [jak: Zobrazit příkazy Store](https://msdn.microsoft.com/library/f9771c6e-3b62-4b24-a5d4-55d68e14fa79).  
  
-   Vnořené dotazy na Entity SQL na serveru může vytvořit spojení a může vrátit velký počet řádků.  
  
     Následuje příklad vnořeného dotazu v klauzuli projekce:  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Kromě toho takové dotazy způsobit kanálu dotazu ke generování jednoho dotazu s duplicitních objektů ve vnořené dotazy. Z toho důvodu může jeden sloupec duplicitní více než jednou. V některých databázích, včetně SQL serveru to může způsobit tabulku v databázi TempDB rozrůstá velmi velké, což může snížit výkon serveru. Při spouštění dotazů vnořené měli věnovat pozornost.  
  
-   Všechny dotazy, které vracejí velké množství dat může způsobit snížení výkonu, pokud klient provádí operace, které spotřebovávají prostředky způsobem, který je přímo úměrná velikosti sady výsledků dotazu. V takovém případě zvažte omezení množství dat vrácených dotazem. Další informace najdete v tématu [jak: Výsledky stránky pomocí dotazu](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030).  
  
 Všechny příkazy automaticky vygenerovaným rozhraním Entity Framework, může být složitější než podobné příkazy napsané explicitně vývojář databáze. Pokud je nutné explicitní kontrolu nad na příkazy provedené na zdroj dat, vezměte v úvahu definování mapování funkce vracející tabulku nebo uložené procedury.  
  
#### <a name="relationships"></a>Relace  
 Pro optimální výkon dotazů je nutné definovat vztahy mezi entitami jako přidružení v modelu entity i logické vztahy ve zdroji dat.  
  
### <a name="query-paths"></a>Dotaz cesty  
 Ve výchozím nastavení se při spouštění <xref:System.Data.Objects.ObjectQuery%601>, související objekty nebudou zobrazeny (i když jsou objekty, které představují samotné vztahy). Můžete načíst související objekty v jednom ze tří způsobů:  
  
1.  Nastavte cestu dotazu před <xref:System.Data.Objects.ObjectQuery%601> provádí.  
  
2.  Volání `Load` metodu na navigační vlastnost, která zveřejňuje objektu.  
  
3.  Nastavte <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> možnost <xref:System.Data.Objects.ObjectContext> k `true`. Všimněte si, že to se provádí automaticky při generování kódu na objektové vrstvě pomocí [Entity Data Model Designer](https://msdn.microsoft.com/library/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf). Další informace najdete v části [vygeneruje kód přehled](https://msdn.microsoft.com/library/6a88ea38-6a90-4107-bc33-531b79ce5b6a).  
  
 Pokud zvažujete možnost, mějte na paměti, že je kompromis mezi počet požadavků na databázi a množství dat vrácené v jediném dotazu. Další informace najdete v tématu [načítání související objekty](https://msdn.microsoft.com/library/452347d2-7b3b-44cd-9001-231299a28cb1).  
  
#### <a name="using-query-paths"></a>Pomocí dotazu cest  
 Cesty k dotazu definovat grafu objektů, které dotaz vrátí. Při definování cestu dotazu pouze jeden požadavek na databázi je nutné pro navrácení všechny objekty, které definuje cestu. Pomocí dotazu cesty může způsobit komplexní příkazy prováděný zdroji dat z objektu zdánlivě jednoduché dotazů. K tomu dochází, protože jeden nebo více spojení jsou nutné k vrácení souvisejících objektů v jediném dotazu. Tato složitost je větší v dotazech pro model komplexní entity, jako je například entitu s dědičnosti nebo cestu, která obsahuje vztahy many-to-many.  
  
> [!NOTE]
>  Použití <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metoda zobrazíte příkaz, který vygeneruje <xref:System.Data.Objects.ObjectQuery%601>. Další informace najdete v tématu [jak: Zobrazit příkazy Store](https://msdn.microsoft.com/library/f9771c6e-3b62-4b24-a5d4-55d68e14fa79).  
  
 Pokud cesta dotaz obsahuje příliš mnoho související objekty nebo objekty obsahují příliš mnoho řádků dat, může být zdroje dat nelze dokončit dotaz. K tomu dochází, pokud dotaz vyžaduje zprostředkující dočasné úložiště, které překračují možnosti datového zdroje. Pokud k tomu dojde, můžete snížit složitost dotazu na datový zdroj explicitně načítání souvisejících objektů.  
  
#### <a name="explicitly-loading-related-objects"></a>Načítají se explicitně související objekty  
 Můžete explicitně načíst související objekty voláním `Load` metodu na navigační vlastnost, která vrátí <xref:System.Data.Objects.DataClasses.EntityCollection%601> nebo <xref:System.Data.Objects.DataClasses.EntityReference%601>. Explicitně načítání objektů vyžaduje k databázi pokaždé, když `Load` je volána.  
  
> [!NOTE]
>  Při volání `Load` při opakování ve smyčce přes kolekce vrácených objektů, jako je například při použití `foreach` – příkaz (`For Each` v jazyce Visual Basic), zprostředkovatele specifická pro zdroj dat musí podporovat více sad výsledků aktivní v rámci jednoho připojení. Pro databáze SQL serveru, musíte zadat hodnotu `MultipleActiveResultSets = true` v připojovacím řetězci zprostředkovatele.  
  
 Můžete také použít <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> metoda při žádné <xref:System.Data.Objects.DataClasses.EntityCollection%601> nebo <xref:System.Data.Objects.DataClasses.EntityReference%601> vlastnosti u entit. To je užitečné, pokud používáte entity POCO.  
  
 I když explicitně načítání související objekty se sníží počet klauzulí JOIN a snížit objem redundantních dat `Load` vyžaduje opakované připojení k databázi, která může být nákladné při načítání explicitně velký počet objektů.  
  
### <a name="saving-changes"></a>Ukládají se změny  
 Při volání <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metoda <xref:System.Data.Objects.ObjectContext>, samostatné vytvoření, aktualizace nebo odstranění příkaz je vygenerována pro každý objekt přidaný, aktualizovaných nebo odstraněných v kontextu. Tyto příkazy jsou provedeny ve zdroji dat v rámci jedné transakce. Jak pomocí dotazů, výkon vytvořit, aktualizovat a odstraňovat operace závisí na složitosti mapování v konceptuálním modelu.  
  
### <a name="distributed-transactions"></a>Distribuované transakce  
 Operace v explicitní transakci, které vyžadují prostředky, které se spravují přes koordinátor distribuovaných transakcí (DTC) bude mnohem dražší než podobné operace, která nevyžaduje službu. Povýšení na DTC proběhnou v následujících situacích:  
  
-   Explicitní transakce pomocí operace databáze systému SQL Server 2000 nebo jiný zdroj dat, která vždy zvýšit úroveň explicitní transakce na DTC.  
  
-   Explicitní transakce pomocí operace SQL Server 2005 při připojení je spravován [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. K tomu dochází, SQL Server 2005 povýší na DTC pokaždé, když je připojení zavřít a znovu otevřít v rámci jedné transakce, což je výchozí chování [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Tato propagační akce DTC nedojde při použití systému SQL Server 2008. Abyste předešli této propagační akce, při použití systému SQL Server 2005, musíte explicitně otevřít a ukončete připojení v rámci transakce. Další informace najdete v tématu [Správa připojení a transakce](https://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
 Explicitní transakce se používá při spuštění jedné nebo více operací uvnitř <xref:System.Transactions> transakce. Další informace najdete v tématu [Správa připojení a transakce](https://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="strategies-for-improving-performance"></a>Strategie pro zlepšení výkonu  
 Pomocí následujících strategií, lze vylepšit výkon dotazů v Entity Framework.  
  
#### <a name="pre-generate-views"></a>Předem vygenerovat zobrazení  
 Generování zobrazení založené na modelu entity je poprvé, že se aplikace spustí dotaz výrazně šetřit náklady. Pomocí nástroje EdmGen.exe předem vygenerovat zobrazení jako soubor kódu jazyka Visual Basic nebo C#, který se dají přidat do projektu během návrhu. Toolkit transformace šablony textu můžete také použít ke generování předem kompilovaných zobrazení. Předem vygenerovaných zobrazení se ověřují v době běhu k zajištění, že jsou v souladu s aktuální verzí zadané entity model. Další informace najdete v tématu [jak: Předběžně generovat zobrazení pro zlepšení výkonu dotazů](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579) a [izolaci výkonu pomocí předkompilovaných/Předprodukčním-generated zobrazení v rozhraní Entity Framework 4](https://go.microsoft.com/fwlink/?LinkID=201337&clcid=0x409).  
  
 Při práci s velmi velkých modelů, platí následující úvahy:  
  
 Formát metadat .NET omezuje počet znaků řetězce uživatele v dané binárního souboru ke 16 777 215 (0xFFFFFF). Pokud jsou generování zobrazení modelu velmi velké a zobrazit soubor dosáhne tohoto limitu, zobrazí se "již není logické místo vytvoření dalších uživatelských řetězců." Chyba kompilace. Tato velikost omezení se vztahuje na všechny spravované binární soubory. Další informace najdete v článku [blogu](https://go.microsoft.com/fwlink/?LinkId=201476) , který ukazuje, jak se vyhnout chybu při práci s velkých a složitých modelů.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Zvažte použití možností sloučení NoTracking pro dotazy  
 Je nutné ke sledování objektů vrácených v kontextu objektu. Detekce změn k objektům a zajištění, že více požadavků pro stejnou logická entita vrátí stejnou instanci objektu vyžaduje, aby objekty připojit k <xref:System.Data.Objects.ObjectContext> instance. Pokud nemáte v plánu provést aktualizace nebo odstranění objektů a nevyžadují, aby Správa identit, zvažte použití <xref:System.Data.Objects.MergeOption.NoTracking> možnosti sloučení, při spouštění dotazů.  
  
#### <a name="return-the-correct-amount-of-data"></a>Vraťte správný objem dat  
 V některých scénářích zadání cesty dotazu pomocí <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metoda je mnohem rychlejší, protože vyžaduje menší počet zpátečních cest k databázi. Ale v jiných scénářích další zpátečních cest k databázi se načíst související objekty může být rychlejší protože jednodušší dotazy s menším počtem spojení za následek méně redundance dat. Z tohoto důvodu doporučujeme vám, že provedete test výkonu různých způsobů, jak načíst související objekty. Další informace najdete v tématu [načítání související objekty](https://msdn.microsoft.com/library/452347d2-7b3b-44cd-9001-231299a28cb1).  
  
 Aby se zabránilo vrátil příliš mnoho dat v jediném dotazu, vezměte v úvahu stránkování výsledků dotazu do více zvládnutelných skupin. Další informace najdete v tématu [jak: Výsledky stránky pomocí dotazu](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030).  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>Omezit rozsah objektu ObjectContext  
 Ve většině případů byste měli vytvořit <xref:System.Data.Objects.ObjectContext> instance v rámci `using` – příkaz (`Using…End Using` v jazyce Visual Basic). To může zvýšit výkon tím, že zajišťuje, že prostředky přidružené ke kontextu objektu jsou automaticky odstraněny při kód ukončení bloku příkazu. Ale při vázání ovládacích prvků u objektů spravovaných kontextu objektu <xref:System.Data.Objects.ObjectContext> instance by se měl zachovat jako vazby je potřeba a odstraněny ručně. Další informace najdete v tématu [Správa připojení a transakce](https://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Zvažte otevření připojení k databázi ručně  
 Když vaše aplikace spustí řadu dotazy objektu nebo často volá <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> zachovat vytvářet, aktualizovat a odstraňovat operace pro zdroj dat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] musí neustále otevření a zavření připojení ke zdroji dat. V těchto situacích zvažte ručně otevření připojení při spuštění těchto operací a zavření nebo rušení připojení po dokončení operace. Další informace najdete v tématu [Správa připojení a transakce](https://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="performance-data"></a>Údaje o výkonu  
 Některá data o výkonu pro Entity Framework je publikováno v následujících příspěvcích [blog týmu ADO.NET](https://go.microsoft.com/fwlink/?LinkId=91905):  
  
-   [Zkoumání výkonu technologie ADO.NET Entity Framework – část 1](https://go.microsoft.com/fwlink/?LinkId=123907)  
  
-   [Zkoumání výkonu technologie ADO.NET Entity Framework – část 2](https://go.microsoft.com/fwlink/?LinkId=123909)  
  
-   [ADO.NET Entity Framework Performance Comparison](https://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>Viz také:
- [Důležité informace o vývoji a nasazení](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
