---
title: Aspekty migrace (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: b6224dcf883daef7b35ef50b7556fc568e433a46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034031"
---
# <a name="migration-considerations-entity-framework"></a>Aspekty migrace (Entity Framework)
[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework poskytuje několik výhod do stávající aplikace. Jeden z nejpoužívanějších důležité tyto výhody je schopnost oddělit struktury dat používané aplikace ze schématu ve zdroji dat pomocí konceptuálního modelu. To umožňuje snadno vytvářet budoucí změny model úložiště nebo zdroj dat bez kompenzační změn aplikace. Další informace o výhodách používání [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], naleznete v tématu [přehled Entity Framework](../../../../../docs/framework/data/adonet/ef/overview.md) a [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Abyste mohli využívat výhody [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], můžete migrovat do existující aplikaci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Některé úlohy jsou společné pro všechny migrované aplikace. Zahrnout tyto běžné úlohy upgradu aplikace pro použití [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] od verze 3.5 Service Pack 1 (SP1), definování modely a mapování a konfigurace technologie Entity Framework. Když migrujete aplikaci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], některé další aspekty, které se vztahují. Tyto aspekty závisí na typu aplikace migruje a na konkrétní funkce aplikace. Toto téma obsahuje informace, které vám pomůžou vybrat nejlepší metodou k použití při upgradu existující aplikaci.  
  
## <a name="general-migration-considerations"></a>Obecné aspekty  
 Při migraci jakékoli aplikace, platí následující aspekty [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
- Všechny aplikace používající [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] od verze 3.5 SP1 je možné migrovat do rozhraní Entity Framework, tak dlouho, dokud zprostředkovatel dat pro zdroj dat, který používá aplikace podporuje rozhraní Entity Framework.  
  
- Entity Framework nemusí podporovat všechny funkce, které jsou součástí Zprostředkovatel zdroje dat, i v případě, že tento zprostředkovatel podporuje rozhraní Entity Framework.  
  
- Pro velké nebo složité aplikace není nutné migrovat celou aplikaci k Entity Frameworku najednou. Ale musí být libovolné části aplikace, která nepoužívá rozhraní Entity Framework změnit stále při změně zdroje dat.  
  
- Datové připojení zprostředkovatele používat Entity Framework můžete sdílet s jinými částmi aplikace, protože [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] používá [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] zprostředkovatele dat pro přístup ke zdroji dat. Například poskytovatel Sqlclienta se používá rozhraním Entity Framework pro přístup k databázi serveru SQL Server. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Běžné úlohy migrace  
 Cesta k migraci do existující aplikaci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] závisí na typu aplikace i na stávající strategie přístupu data. Však můžete vždycky musí provádět následující úkoly při migraci do existující aplikaci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  Všechny tyto úlohy provádějí automaticky při použití nástroje modelu Entity Data Model od verze Visual Studio 2008. Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
1. Upgrade aplikace.  
  
     Projekt vytvořený pomocí dřívější verze sady Visual Studio a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] musí být upgradována na Visual Studio 2008 SP1 a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] od verze 3.5 SP1.  
  
2. Definujte modely a mapování.  
  
     Modelu a souborů mapování definování entity v konceptuálním modelu; struktury ve zdroji dat, jako jsou tabulky, uložené procedury a zobrazení a mapování mezi entitami a datových struktur zdroje. Další informace najdete v tématu [jak: Ručně definovat modelu a mapování souborů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).  
  
     Názvy objektů ve zdroji dat musí odpovídat typy, které jsou definovány v modelu úložiště. Pokud stávající aplikace jednotlivě vystavuje dat jako objektů, je třeba zajistit, že entit a vlastnosti, které jsou definované v konceptuálním modelu shodovat s názvy těchto existující datové třídy a vlastnosti. Další informace najdete v tématu [jak: Přizpůsobení modelování a mapování souborů pro práci s vlastní objekty](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100)).  
  
    > [!NOTE]
    >  Entity Data Model Designer je možné přejmenovat entit v konceptuálním modelu tak, aby odpovídala stávající objekty. Další informace najdete v tématu [Entity Data Model Designer](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)).  
  
3. Definujte připojovací řetězec.  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Pomocí speciálně formátovaného připojovací řetězec při provádění dotazů u konceptuálního modelu. Tento připojovací řetězec zapouzdřuje informace o modelu a souborů mapování a připojení ke zdroji dat. Další informace najdete v tématu [jak: Definujte připojovací řetězec](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md).  
  
4. Konfigurace projektu Visual Studio.  
  
     Odkazy na [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sestavení a modelu a mapování soubory musí být přidány do projektu sady Visual Studio. Tyto soubory mapování můžete přidat do projektu zajistit, že jsou nasazené v aplikaci v umístění, které je uvedené v připojovacím řetězci. Další informace najdete v tématu [jak: Ruční konfigurace projektu v Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Důležité informace týkající se aplikací pomocí existujících objektů  
 Počínaje [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] podporuje "plain old" CLR objektů POCO, tzv ignorujících objekty. Ve většině případů můžete pracovat existujících objektů [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] tím, že menší změny. Další informace najdete v tématu [práce s entitami objektů POCO](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100)). Můžete také migrovat aplikace do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a použití datových tříd, které jsou generovány pomocí nástroje Entity Framework. Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Důležité informace týkající se aplikací, které používají zprostředkovatele ADO.NET  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] poskytovatelé, například SqlClient, umožňují dotazování na zdroj dat pro vrácení tabulkových dat. Je také možné načíst data do [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] datové sady. Následující seznam popisuje důležité aspekty upgradu aplikace, která využívá existující [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] zprostředkovatele:  
  
- Zobrazení tabulky dat pomocí čtečky dat.  

  Můžete zvážit spouštění [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazování pomocí zprostředkovatel EntityClient a vytváření výčtů vráceného <xref:System.Data.EntityClient.EntityDataReader> objektu. Pouze v případě, že vaše aplikace obsahuje tabulková data pomocí čtecí modul dat a nevyžaduje, aby zařízení poskytovaných [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pro materializaci dat do objektů, sledování změn a provádění aktualizací. Můžete dál používat existující kód přístupu k datům, který zpřístupňuje aktualizace ke zdroji dat, ale můžete použít stávající připojení k němu přistupovat z <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> vlastnost <xref:System.Data.EntityClient.EntityConnection>. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
- Práce s datovými sadami.  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Poskytuje řadu stejné funkce poskytované datové sady, včetně stálost v paměti, řešení change tracking, datové vazby a serializaci objektů jako XML data. Další informace najdete v tématu [práce s objekty](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
  Pokud [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] neposkytuje funkce pro datové sady, které vaše aplikace vyžaduje, můžete stále využití výhod dotazů LINQ s použitím [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]. Další informace najdete v tématu [LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Důležité informace týkající se aplikací, které vytvoření vazby dat k ovládacím prvkům  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Umožňuje zapouzdření dat ve zdroji dat, jako datové sady nebo s [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] data správy zdrojového kódu a na tyto ovládací prvky dat svážou prvky uživatelského rozhraní. Následující seznam popisuje důležité informace týkající se vytvoření vazby ovládacích prvků k datům Entity Framework.  
  
- Vazba dat k ovládacím prvkům.  

  Při dotazování konceptuální model, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vrátí data jako objekty, které jsou instancemi typů entit. Tyto objekty mohou být vázány přímo na ovládací prvky a tato vazba podporuje aktualizace. To znamená, že změny dat v ovládacím prvku, jako je například řádek v <xref:System.Windows.Forms.DataGridView>, automaticky uloženy do databáze při <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metoda je volána.  
  
  Pokud vaše aplikace zobrazí výsledky dotazu pro zobrazení dat v <xref:System.Windows.Forms.DataGridView> nebo jiný typ ovládacího prvku, který podporuje datovou vazbu, můžete upravit svou aplikaci k vytvoření vazby ovládacího prvku na výsledek <xref:System.Data.Objects.ObjectQuery%601>.  
  
  Další informace najdete v tématu [vazby objektů k ovládacím prvkům](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100)).  
  
- [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] ovládací prvky zdroje dat  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsahuje ovládací prvek zdroje dat navržené pro zjednodušení datové vazby v [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] webové aplikace. Další informace najdete v tématu [Přehled ovládacího prvku webového serveru EntityDataSource](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100)).  
  
## <a name="other-considerations"></a>Ostatní úvahy  
 Tady jsou důležité informace, které jim umožňují uplatnit při migraci konkrétní typy aplikací, aby rozhraní Entity Framework.  
  
- Aplikace, které zpřístupňují služby pro data.  

  Webové služby a aplikace, které jsou založené na Windows Communication Foundation (WCF) zpřístupňují data z podkladového zdroje dat s využitím formátu XML pro zasílání zpráv žádost odpověď. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Podporuje serializaci objektů entit pomocí binárního souboru XML, nebo WCF data smlouvy serializace. Binární soubor a WCF serializace podporují úplné serializace grafů objektů. Další informace najdete v tématu [vytváření vícevrstvých aplikací](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100)).  
  
- Aplikace, které používají XML data.  

  Serializace objektu umožňuje vytvářet [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] datové služby. Tyto služby poskytují data aplikací, které využívají data XML, jako jsou založené na AJAX internetových aplikací. V těchto případech zvažte použití [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]. Tyto datové služby jsou založené na modelu Entity Data Model a poskytovat dynamické přístup k datům entity pomocí standardního Representational State Transfer (REST) HTTP akce, jako například GET, PUT a publikovat. Další informace najdete v tématu [4.5 služby WCF Data](../../../../../docs/framework/data/wcf/index.md).  
  
  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nepodporuje datový typ native XML. To znamená, že pokud entita je namapována na tabulku se sloupcem XML, vlastnost ekvivalentní entity pro sloupec typu XML je řetězec. Objekty lze odpojen a serializovanou jako XML. Další informace najdete v tématu [serializaci objektů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
  Pokud vaše aplikace vyžaduje schopnost dotazovat XML data, můžete stále využít výhod výhody dotazů LINQ pomocí LINQ to XML. Další informace najdete v tématu [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) nebo [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
- Aplikace, které udržují stav.  

  [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Webové aplikace, často musíte mít stavu webové stránky nebo uživatelské relace. Objekty ve <xref:System.Data.Objects.ObjectContext> instance mohou být uloženy v zobrazení stavu klienta nebo ve stavu relace na serveru a později načíst a znovu připojit nový kontext objektu. Další informace najdete v tématu [připojení a odpojení objekty](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o nasazení](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Terminologie Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)
