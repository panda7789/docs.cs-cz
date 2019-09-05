---
title: Předpoklady migrace (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: 3554f530acf0e3ca3e66dddf74f63e7ede03708e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248556"
---
# <a name="migration-considerations-entity-framework"></a>Předpoklady migrace (Entity Framework)
ADO.NET Entity Framework poskytuje několik výhod pro existující aplikaci. Jedním z nejdůležitějších z těchto výhod je možnost použít koncepční model k oddělení datových struktur používaných aplikací ze schématu ve zdroji dat. Díky tomu můžete snadno provádět budoucí změny modelu úložiště nebo samotného zdroje dat, aniž byste museli provádět kompenzační změny aplikace. Další informace o výhodách použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]naleznete v tématu [Entity Framework Overview](overview.md) a [model EDM (Entity Data Model)](../entity-data-model.md).  
  
 Chcete-li využít výhod [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ,můžetemigrovatexistujícíaplikacina.[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Některé úlohy jsou společné pro všechny migrované aplikace. Mezi tyto běžné úlohy patří upgrade aplikace na použití .NET Framework od verze 3,5 Service Pack 1 (SP1), definování modelů a mapování a konfigurace Entity Framework. Při migraci aplikace do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]nástroje jsou k dispozici další předpoklady. Tyto požadavky závisí na typu migrované aplikace a na konkrétních funkcích aplikace. Toto téma poskytuje informace, které vám pomůžou vybrat nejlepší přístup k použití při upgradu existující aplikace.  
  
## <a name="general-migration-considerations"></a>Obecné předpoklady migrace  
 Při migraci jakékoli aplikace do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]nástroje platí následující požadavky:  
  
- Všechny aplikace, které používají .NET Framework počínaje verzí 3,5 SP1, lze migrovat do Entity Framework, pokud poskytovatel dat pro zdroj dat používaný aplikací podporuje Entity Framework.  
  
- Entity Framework nemusí podporovat všechny funkce zprostředkovatele zdrojů dat, a to i v případě, že tento zprostředkovatel podporuje Entity Framework.  
  
- Pro velkou nebo složitou aplikaci není nutné migrovat celou aplikaci na Entity Framework najednou. Nicméně jakákoli část aplikace, která nepoužívá Entity Framework, musí být při změně zdroje dat stále změněna.  
  
- Připojení zprostředkovatele dat používaného Entity Framework lze sdílet s ostatními částmi aplikace, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] protože používá poskytovatele dat ADO.NET pro přístup ke zdroji dat. Například poskytovatel SqlClient používá Entity Framework k přístupu k databázi SQL Server. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Běžné úlohy migrace  
 Cesta k migraci existující aplikace na [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] závisí na typu aplikace i na stávající strategii přístupu k datům. Při migraci existující aplikace do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]nástroje je však nutné vždy provést následující úlohy.  
  
> [!NOTE]
> Všechny tyto úlohy jsou prováděny automaticky při použití model EDM (Entity Data Model)ch nástrojů počínaje sadou Visual Studio 2008. Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).  
  
1. Upgradujte aplikaci.  
  
     Projekt vytvořený pomocí starší verze sady Visual Studio a .NET Framework musí být upgradován tak, aby používal sadu Visual Studio 2008 SP1 a .NET Framework počínaje verzí 3,5 SP1.  
  
2. Definujte modely a mapování.  
  
     Model a mapovací soubory definují entity v koncepčním modelu; struktury ve zdroji dat, jako jsou tabulky, uložené procedury a zobrazení; a mapování mezi entitami a strukturami zdrojů dat. Další informace najdete v tématu [jak: Ručně definujte model a mapovací soubory](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).  
  
     Typy, které jsou definovány v modelu úložiště, musí odpovídat názvům objektů ve zdroji dat. Pokud existující aplikace zveřejňuje data jako objekty, je nutné zajistit, aby entity a vlastnosti, které jsou definovány v koncepčním modelu, odpovídaly názvům těchto existujících datových tříd a vlastností. Další informace najdete v tématu [jak: Přizpůsobení modelování a souborů mapování pro práci s vlastními](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100))objekty.  
  
    > [!NOTE]
    > Model EDM (Entity Data Model) Designer lze použít k přejmenování entit v koncepčním modelu tak, aby odpovídaly existujícím objektům. Další informace najdete v tématu [model EDM (Entity Data Model) Designer](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)).  
  
3. Zadejte připojovací řetězec.  
  
     Při provádění dotazů na koncepční model používáspeciálněformátovanýpřipojovacířetězec.[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Tento připojovací řetězec zapouzdřuje informace o modelu a mapování souborů a připojení ke zdroji dat. Další informace najdete v tématu [jak: Zadejte připojovací řetězec](how-to-define-the-connection-string.md).  
  
4. Nakonfigurujte projekt sady Visual Studio.  
  
     Odkazy na [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sestavení a soubory modelu a mapování musí být přidány do projektu aplikace Visual Studio. Tyto soubory mapování můžete přidat do projektu, aby bylo zajištěno, že budou nasazeny s aplikací v umístění, které je uvedeno v připojovacím řetězci. Další informace najdete v tématu [jak: Ručně nakonfigurujte Entity Framework projekt](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Předpoklady pro aplikace s existujícími objekty  
 Počínaje .NET Framework 4 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] podporuje "" obyčejné staré "objekty CLR (POCO), označované také jako trvalé ignorování objektů. Ve většině případů mohou vaše stávající objekty pracovat s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] tím, že provádějí menší změny. Další informace najdete v tématu [práce s POCO entitami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100)). Můžete také migrovat aplikaci na [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a použít datové třídy, které jsou generovány nástroji Entity Framework. Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Pokyny pro aplikace, které používají poskytovatele ADO.NET  
 ADO.NET poskytovatelé, jako je SqlClient, umožňují dotazovat se na zdroj dat a vracet tabulková data. Data lze také načíst do datové sady ADO.NET. Následující seznam popisuje požadavky na upgrade aplikace, která používá existujícího poskytovatele ADO.NET:  
  
- Zobrazení tabulkových dat pomocí čtecího modulu dat.  

  Můžete zvážit provedení [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazu pomocí poskytovatele EntityClient a vytvoření výčtu prostřednictvím vráceného <xref:System.Data.EntityClient.EntityDataReader> objektu. Tuto možnost proveďte pouze v případě, že vaše aplikace zobrazuje tabulková data pomocí čtecího modulu dat a nevyžaduje funkce [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] poskytované pro vyhodnocování data do objektů, sledování změn a provádění aktualizací. Můžete dál používat stávající přístup k datům, který umožňuje aktualizace zdroje dat, ale můžete použít stávající připojení, ke kterému se přistupuje z <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> <xref:System.Data.EntityClient.EntityConnection>vlastnosti. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
- Práce s datovými sadami.  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Poskytuje mnoho stejných funkcí poskytovaných datovou sadou, včetně trvalosti v paměti, sledování změn, datových vazeb a serializace objektů jako XML data. Další informace naleznete v tématu [práce s objekty](working-with-objects.md).  
  
  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Pokud neposkytuje funkci datové sady, kterou vaše aplikace potřebuje, můžete přesto využít výhod dotazů LINQ pomocí LINQ to DataSet. Další informace najdete v tématu [LINQ to DataSet](../linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Pokyny pro aplikace, které vážou data s ovládacími prvky  
 .NET Framework umožňuje zapouzdřit data ve zdroji dat, jako je například datová sada nebo ovládací prvek zdroje dat ASP.NET, a následně navazovat prvky uživatelského rozhraní na tyto datové ovládací prvky. Následující seznam popisuje, jak svázat ovládací prvky s Entity Frameworkmi daty.  
  
- Svázání dat s ovládacími prvky.  

  Při dotazování konceptuálního modelu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vrací data jako objekty, které jsou instancemi typů entit. Tyto objekty mohou být vázány přímo na ovládací prvky a tato vazba podporuje aktualizace. To znamená, že změny dat v ovládacím prvku, jako je například řádek v <xref:System.Windows.Forms.DataGridView>, jsou automaticky uloženy do databáze <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> při volání metody.  
  
  Pokud vaše aplikace vytvoří výčet výsledků dotazu pro zobrazení dat v <xref:System.Windows.Forms.DataGridView> nebo jiném typu ovládacího prvku, který podporuje datovou vazbu, můžete upravit aplikaci pro svázání ovládacího prvku s výsledkem. <xref:System.Data.Objects.ObjectQuery%601>  
  
  Další informace naleznete v tématu [vázání objektů k ovládacím prvkům](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100)).  
  
- Ovládací prvky zdroje dat ASP.NET.  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsahuje ovládací prvek zdroje dat navržený pro zjednodušení datových vazeb ve webových aplikacích v ASP.NET. Další informace najdete v tématu [Přehled ovládacího prvku webový server EntityDataSource](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100)).  
  
## <a name="other-considerations"></a>Ostatní úvahy  
 Níže jsou uvedeny předpoklady, které mohou být uplatněny při migraci konkrétních typů aplikací na Entity Framework.  
  
- Aplikace, které zveřejňují datové služby.  

  Webové služby a aplikace, které jsou založeny na Windows Communication Foundation (WCF) zveřejňují data z podkladového zdroje dat pomocí formátu zasílání zpráv požadavku a odpovědí XML. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Podporuje serializaci objektů entit pomocí binární, XML nebo serializace kontraktu dat WCF. Binární a serializace WCF podporují úplnou serializaci grafů objektů. Další informace najdete v tématu [vytváření N-vrstvých aplikací](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100)).  
  
- Aplikace, které používají data XML.  

  Serializace objektů umožňuje vytvářet [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] datové služby. Tyto služby poskytují data aplikacím, které využívají data XML, jako jsou například internetové aplikace založené na AJAX. V těchto případech zvažte použití nástroje [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]. Tyto datové služby jsou založené na model EDM (Entity Data Model) a poskytují dynamický přístup k datům entit pomocí akcí protokolu HTTP Standard representational state transfer (REST), jako například GET, PUT a POST. Další informace najdete v tématu [4.5 služby WCF Data](../../wcf/index.md).  
  
  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nepodporuje datový typ native-XML. To znamená, že když je entita namapována na tabulku se sloupcem XML, je ekvivalentní vlastnost entity pro sloupec XML řetězec. Objekty mohou být odpojeny a serializovány jako XML. Další informace naleznete v tématu [serializace objektů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
  Pokud vaše aplikace vyžaduje možnost dotazování na data XML, můžete i nadále využít výhod dotazů LINQ pomocí LINQ to XML. Další informace najdete v tématu [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) nebo [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
- Aplikace, které udržují stav.  

  Webové aplikace ASP.NET musí často udržovat stav webové stránky nebo uživatelské relace. Objekty v <xref:System.Data.Objects.ObjectContext> instanci lze uložit ve stavu zobrazení klienta nebo ve stavu relace na serveru a později načíst a znovu připojit k novému kontextu objektu. Další informace najdete v tématu [připojení a odpojení objektů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o nasazení](deployment-considerations.md)
- [Terminologie Entity Framework](terminology.md)
