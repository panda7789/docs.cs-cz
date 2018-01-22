---
title: "Posouzení migrace (rozhraní Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8e4c1b06e5a3a7717b99379fd9bca2c5a8a14a6a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="migration-considerations-entity-framework"></a>Posouzení migrace (rozhraní Entity Framework)
[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework poskytuje několik výhod do existující aplikace. Jedním z nejčastěji důležitá z těchto výhod je schopnost používat konceptuální model k oddělení používá aplikace ze schématu ve zdroji dat datové struktury. To umožňuje vám umožní snadno provádět budoucí změny do úložiště modelu nebo ke zdroji dat bez zušlechtěných změn do aplikace. Další informace o výhodách používání [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], najdete v části [Entity Framework přehled](../../../../../docs/framework/data/adonet/ef/overview.md) a [datového modelu Entity](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Abyste mohli využívat výhod [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], můžete migrovat do existující aplikaci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Některé úlohy jsou společné pro všechny migrované aplikace. Tyto běžné úlohy zahrnovat upgrade aplikace pro používání [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] od verze 3.5 Service Pack 1 (SP1), definování modely a mapování a konfigurace rozhraní Entity Framework. Při migraci aplikaci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], existují další důležité informace, které se vztahují. Tyto aspekty závisí na typu aplikace se migruje a na specifické funkce aplikace. Toto téma obsahuje informace, které vám pomůžou vybrat nejlepší metodou k použití při upgradu existující aplikaci.  
  
## <a name="general-migration-considerations"></a>Migrace Obecné aspekty  
 Při migraci jakékoli aplikace, platí následující aspekty [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
-   Všechny aplikace, která používá [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] od verze 3.5 SP1 se dají migrovat na rozhraní Entity Framework, poskytovatel dat pro zdroj dat, který je používán aplikace podporuje rozhraní Entity Framework.  
  
-   Rozhraní Entity Framework nemusí podporovat všechny funkce Zprostředkovatel zdroje dat, i v případě, že zprostředkovatel nepodporuje Entity Framework.  
  
-   Pro aplikaci velká nebo složitá není nutné migrovat celou aplikaci na rozhraní Entity Framework najednou. Ale libovolná součást aplikace, která nepoužívá rozhraní Entity Framework musí stále změnit, pokud zdroj dat změny.  
  
-   Připojení poskytovatele dat, používá rozhraní Entity Framework můžete sdílet s dalšími částmi vaší aplikace, protože [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] používá [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] zprostředkovatelé dat pro přístup ke zdroji dat. Poskytovatel Sqlclienta se používá například rozhraní Entity Framework pro přístup k databázi systému SQL Server. Další informace najdete v tématu [zprostředkovatel EntityClient rozhraní Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Běžné úlohy migrace  
 Cesta k migraci do existující aplikaci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] závisí na typu aplikace i na stávající strategie přístupu data. Však musí vždy provést následující úlohy při migraci do existující aplikaci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  Všechny tyto úlohy se provádí automaticky při použití nástroje modelu Entity Data Model počínaje [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)]. Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
1.  Upgrade aplikace.  
  
     Projekt vytvořený pomocí dřívější verzi [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] používat, musí být upgradován [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)] SP1 a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] od verze 3.5 SP1.  
  
2.  Definujte modely a mapování.  
  
     Model a mapování souborů definovat entity v konceptuálním modelu; struktury v zdroji dat, jako jsou tabulky, uložené procedury a zobrazení; a mapování mezi struktury zdrojové entity a data. Další informace najdete v tématu [postupy: ruční definování modelu a mapování souborů](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a).  
  
     Typy, které jsou definované v modelu úložiště musí odpovídat názvu objektů v datovém zdroji. Pokud stávající aplikace zpřístupní data jako objekty, je třeba zajistit, že entit a vlastnosti, které jsou definované v konceptuálním modelu odpovídat názvům těchto existující datové třídy a vlastnosti. Další informace najdete v tématu [postupy: přizpůsobení modelování a mapování souborů na práci s objekty vlastní](http://msdn.microsoft.com/library/bb40c4db-0121-4e45-a167-8fb06707a708).  
  
    > [!NOTE]
    >  Entity Data Model Designer můžete použít k přejmenování entity v konceptuálním modelu tak, aby odpovídala stávající objekty. Další informace najdete v tématu [Entity Data Model Designer](http://msdn.microsoft.com/library/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf).  
  
3.  Definujte připojovací řetězec.  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Používá speciálně formátovaný připojovací řetězec při provádění dotazů vůči konceptuálního modelu. Tento připojovací řetězec zapouzdří informace o modelu a soubory mapování a připojení ke zdroji dat. Další informace najdete v tématu [postupy: definování připojovací řetězec](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md).  
  
4.  Konfigurace [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] projektu.  
  
     Odkazuje na [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sestavení a modelu a mapování soubory musí být přidány do [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] projektu. Tyto soubory mapování můžete přidat do projektu zajistit, aby byly nasazené aplikace v umístění, které je uvedené v připojovacím řetězci. Další informace najdete v tématu [postupy: ruční konfigurace projektu Entity Framework](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Důležité informace pro aplikace s existující objekty  
 Počínaje [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] podporuje "prostý starý" objekty CLR (objektů POCO), které ignorují trvalost objekty nazývané také. Ve většině případů můžete pracovat stávající objekty [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] tím, že menší změny. Další informace najdete v tématu [práce s entity objektů POCO](http://msdn.microsoft.com/library/5e0fb82a-b6d1-41a1-b37b-c12db61629d3). Můžete také migrovat aplikaci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a používat datové třídy, které jsou generovány nástrojem nástroje Entity Framework. Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Důležité informace týkající se aplikací, které používají zprostředkovatele ADO.NET  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]poskytovatelé, například SqlClient, umožňují dotaz na zdroj dat vrátit tabulkové data. Je také možné načíst data do [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] datovou sadu. Následující seznam popisuje důležité informace týkající se upgradu aplikace, která používá stávající [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] zprostředkovatele:  
  
 Zobrazení tabulková data pomocí čtecí modul dat.  
 Můžete zvážit při spouštění [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazu pomocí zprostředkovatel EntityClient a výčet prostřednictvím vráceného <xref:System.Data.EntityClient.EntityDataReader> objektu. Provést pouze v případě, že vaše aplikace zobrazí tabulková data pomocí čtecí modul dat a nevyžaduje, aby zařízení, které jsou ve [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pro vyhodnocování data do objektů, sledování změn a provedení aktualizací. Můžete nadále používat existující data přístupový kód, který provede aktualizace zdroje dat, ale můžete použít existující připojení k němu přistupovat z <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> vlastnost <xref:System.Data.EntityClient.EntityConnection>. Další informace najdete v tématu [zprostředkovatel EntityClient rozhraní Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 Práce s datovými sadami.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Poskytuje řadu stejné funkce poskytované datovou sadu, včetně trvalost v paměti, změna sledování, datové vazby a serializaci objektů jako XML data. Další informace najdete v tématu [práce s objekty](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Pokud [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] neposkytuje funkci sady dat vyžaduje vaše aplikace, můžete nadále využívat výhod výhod dotazů LINQ s použitím [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]. Další informace najdete v tématu [LINQ na DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Důležité informace pro aplikace, které vazby dat k ovládacím prvkům  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Umožňuje zapouzdření dat ve zdroji dat, jako třeba a datové sady nebo [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] zdroje řízení dat a pak vytvořte vazbu prvky uživatelského rozhraní na tyto ovládací prvky data. Následující seznam popisuje důležité informace týkající se vytvoření vazby ovládacích prvků k datům Entity Framework.  
  
 Vazba dat s ovládacími prvky.  
 Když dotazujete konceptuální model, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vrátí data jako objekty, které jsou instancemi typy entit. Tyto objekty mohou být vázány přímo na ovládací prvky a tuto vazbu podporuje aktualizace. To znamená, že změny dat v ovládacím prvku, jako je například řádek na <xref:System.Windows.Forms.DataGridView>, automaticky ukládány do databáze při <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metoda je volána.  
  
 Pokud vaše aplikace zobrazí výsledky dotazu pro zobrazení dat v <xref:System.Windows.Forms.DataGridView> nebo jiný typ ovládacího prvku, který podporuje datovou vazbu, můžete upravit aplikaci k vytvoření vazby ovládacího prvku na výsledek <xref:System.Data.Objects.ObjectQuery%601>.  
  
 Další informace najdete v tématu [vazby objektů k ovládacím prvkům](http://msdn.microsoft.com/library/2fd34855-929b-4303-a91e-4bb69d958f2b).  
  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]ovládací prvky datových zdrojů.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zahrnuje ovládací prvek zdroje dat, který je navržená tak, aby se zjednodušila datové vazby v [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] webové aplikace. Další informace najdete v tématu [ovládacího prvku zdroje dat Entity Framework](http://msdn.microsoft.com/library/1f09af00-9578-4744-a029-765710a3c83f).  
  
## <a name="other-considerations"></a>Ostatní úvahy  
 Níže jsou uvedeny důležité informace, které se mohou vztahovat při migraci konkrétní typy aplikací, aby rozhraní Entity Framework.  
  
 Aplikace, které zveřejňují datové služby.  
 Webové služby a aplikace, které jsou založené na Windows Communication Foundation (WCF) získal data z příslušný zdroj dat ve formátu XML požadavků a odpovědí zasílání zpráv. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Podporuje pomocí XML, binární serializace objektů entit nebo kontraktů dat WCF serializace. Binární a serializace WCF podporovat úplné serializace objektu grafy. Další informace najdete v tématu [vytváření víceúrovňových aplikací](http://msdn.microsoft.com/library/9439d2ba-6b5f-44e8-be65-8a442d922cbb).  
  
 Aplikace, které používají XML data.  
 Serializace objektu umožňuje vytvářet [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] datové služby. Tyto služby poskytovat data pro aplikace, které využívají data XML, jako je například na základě AJAX Internetové aplikace. V těchto případech, zvažte použití [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]. Tyto datové služby jsou založené na Entity Data Model a zadejte dynamické přístup k datům entity pomocí standardní přenosu REST (Representational State) HTTP akcí, jako například GET, PUT a POST. Další informace najdete v tématu [WCF Data Services 4.5](../../../../../docs/framework/data/wcf/index.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nepodporuje datový typ XML nativní. To znamená, že při entita je namapovaná na tabulku s sloupec XML, je vlastnost ekvivalentní entity pro sloupec typu XML řetězec. Objekty, můžete odpojení a serializovanou jako XML. Další informace najdete v tématu [serializaci objektů](http://msdn.microsoft.com/library/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
 Pokud vaše aplikace vyžaduje schopnost dotazovat XML data, můžete přesto využít výhod dotazů LINQ s použitím technologie LINQ to XML. Další informace najdete v tématu [technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).  
  
 Aplikace, které udržují stavu.  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]Webové aplikace musí často Udržovat stav webové stránky nebo uživatelské relace. Objekty v <xref:System.Data.Objects.ObjectContext> instance dají uložená v zobrazení stavu klienta, nebo ve stavu relace na serveru a později načíst a znovu připojit ke nový kontext objektu. Další informace najdete v tématu [Attaching a odpojení objekty](http://msdn.microsoft.com/library/41d5c1ef-1b78-4502-aa10-7e1438d62d23).  
  
## <a name="see-also"></a>Viz také  
 [Důležité informace o nasazení](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Terminologie Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)
