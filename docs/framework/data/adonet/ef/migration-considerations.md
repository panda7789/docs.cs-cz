---
title: Předpoklady migrace (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: 168aec6ef369f446cfac22ee5c4361fa06aaf16d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569444"
---
# <a name="migration-considerations-entity-framework"></a>Předpoklady migrace (Entity Framework)
ADO.NET Entity Framework poskytuje několik výhod pro existující aplikaci. Jedním z nejdůležitějších z těchto výhod je možnost použít koncepční model k oddělení datových struktur používaných aplikací ze schématu ve zdroji dat. Díky tomu můžete snadno provádět budoucí změny modelu úložiště nebo samotného zdroje dat, aniž byste museli provádět kompenzační změny aplikace. Další informace o výhodách použití Entity Framework najdete v tématu [přehled Entity Framework](overview.md) a [model EDM (Entity Data Model)](../entity-data-model.md).  
  
 Chcete-li využít výhody Entity Framework, můžete do Entity Framework migrovat existující aplikaci. Některé úlohy jsou společné pro všechny migrované aplikace. Mezi tyto běžné úlohy patří upgrade aplikace na použití .NET Framework od verze 3,5 Service Pack 1 (SP1), definování modelů a mapování a konfigurace Entity Framework. Při migraci aplikace do Entity Framework Existují další předpoklady, které je potřeba provést. Tyto požadavky závisí na typu migrované aplikace a na konkrétních funkcích aplikace. Toto téma poskytuje informace, které vám pomůžou vybrat nejlepší přístup k použití při upgradu existující aplikace.  
  
## <a name="general-migration-considerations"></a>Obecné předpoklady migrace  
 Při migraci jakékoli aplikace do Entity Framework platí následující požadavky:  
  
- Všechny aplikace, které používají .NET Framework počínaje verzí 3,5 SP1, lze migrovat do Entity Framework, pokud poskytovatel dat pro zdroj dat používaný aplikací podporuje Entity Framework.  
  
- Entity Framework nemusí podporovat všechny funkce zprostředkovatele zdrojů dat, a to i v případě, že tento zprostředkovatel podporuje Entity Framework.  
  
- Pro velkou nebo složitou aplikaci není nutné migrovat celou aplikaci na Entity Framework najednou. Nicméně jakákoli část aplikace, která nepoužívá Entity Framework, musí být při změně zdroje dat stále změněna.  
  
- Připojení zprostředkovatele dat používaného Entity Framework lze sdílet s ostatními částmi aplikace, protože Entity Framework používá pro přístup ke zdroji dat poskytovatele dat ADO.NET. Například poskytovatel SqlClient používá Entity Framework k přístupu k databázi SQL Server. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Běžné úlohy migrace  
 Cesta k migraci existující aplikace na Entity Framework závisí na typu aplikace i na stávající strategii přístupu k datům. Při migraci existující aplikace do Entity Framework je však nutné vždy provést následující úlohy.  
  
> [!NOTE]
> Všechny tyto úlohy jsou prováděny automaticky při použití model EDM (Entity Data Model)ch nástrojů počínaje sadou Visual Studio 2008. Další informace naleznete v tématu [How to: use the model EDM (Entity Data Model) Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
1. Upgradujte aplikaci.  
  
     Projekt vytvořený pomocí starší verze sady Visual Studio a .NET Framework musí být upgradován tak, aby používal sadu Visual Studio 2008 SP1 a .NET Framework počínaje verzí 3,5 SP1.  
  
2. Definujte modely a mapování.  
  
     Model a mapovací soubory definují entity v koncepčním modelu; struktury ve zdroji dat, jako jsou tabulky, uložené procedury a zobrazení; a mapování mezi entitami a strukturami zdrojů dat. Další informace naleznete v tématu [How to: Manual model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).  
  
     Typy, které jsou definovány v modelu úložiště, musí odpovídat názvům objektů ve zdroji dat. Pokud existující aplikace zveřejňuje data jako objekty, je nutné zajistit, aby entity a vlastnosti, které jsou definovány v koncepčním modelu, odpovídaly názvům těchto existujících datových tříd a vlastností. Další informace najdete v tématu [Postup: přizpůsobení modelování a souborů mapování pro práci s vlastními objekty](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100)).  
  
    > [!NOTE]
    > Model EDM (Entity Data Model) Designer lze použít k přejmenování entit v koncepčním modelu tak, aby odpovídaly existujícím objektům. Další informace najdete v tématu [model EDM (Entity Data Model) Designer](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)).  
  
3. Zadejte připojovací řetězec.  
  
     Entity Framework používá speciálně formátovaný připojovací řetězec při provádění dotazů na koncepční model. Tento připojovací řetězec zapouzdřuje informace o modelu a mapování souborů a připojení ke zdroji dat. Další informace naleznete v tématu [How to: define a Connection String](how-to-define-the-connection-string.md).  
  
4. Nakonfigurujte projekt sady Visual Studio.  
  
     Odkazy na Entity Framework sestavení a model a mapovací soubory musí být přidány do projektu aplikace Visual Studio. Tyto soubory mapování můžete přidat do projektu, aby bylo zajištěno, že budou nasazeny s aplikací v umístění, které je uvedeno v připojovacím řetězci. Další informace naleznete v tématu [How to: ručně configure Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Předpoklady pro aplikace s existujícími objekty  
 Počínaje .NET Framework 4 Entity Framework podporuje "obyčejné staré" objekty CLR (POCO), označované také jako trvalá ignorování objektů. Ve většině případů mohou vaše stávající objekty pracovat s Entity Framework tím, že provádějí menší změny. Další informace najdete v tématu [práce s POCO entitami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100)). Můžete také migrovat aplikaci na Entity Framework a použít datové třídy, které jsou generovány pomocí nástrojů Entity Framework. Další informace naleznete v tématu [How to: use the model EDM (Entity Data Model) Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Pokyny pro aplikace, které používají poskytovatele ADO.NET  
 ADO.NET poskytovatelé, jako je SqlClient, umožňují dotazovat se na zdroj dat a vracet tabulková data. Data lze také načíst do datové sady ADO.NET. Následující seznam popisuje požadavky na upgrade aplikace, která používá existujícího poskytovatele ADO.NET:  
  
- Zobrazení tabulkových dat pomocí čtecího modulu dat.  

  Můžete zvážit provedení [!INCLUDE[esql](../../../../../includes/esql-md.md)]ho dotazu pomocí poskytovatele EntityClient a vytvoření výčtu prostřednictvím vráceného objektu <xref:System.Data.EntityClient.EntityDataReader>. Tuto možnost proveďte pouze v případě, že vaše aplikace zobrazuje tabulková data pomocí čtecího modulu dat a nevyžaduje zařízení poskytovaná Entity Framework pro data vyhodnocování do objektů, sledování změn a provádění aktualizací. Můžete dál používat existující kód pro přístup k datům, který umožňuje aktualizace zdroje dat, ale můžete použít existující připojení, ke kterému se přistupuje z vlastnosti <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> <xref:System.Data.EntityClient.EntityConnection>. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
- Práce s datovými sadami.  

  Entity Framework poskytuje mnoho ze stejných funkcí poskytovaných datovou sadou, včetně trvalost v paměti, sledování změn, datových vazeb a serializace objektů jako XML data. Další informace naleznete v tématu [práce s objekty](working-with-objects.md).  
  
  Pokud Entity Framework neposkytuje funkcionalitu datové sady, kterou vaše aplikace potřebuje, můžete i nadále využívat výhod dotazů LINQ pomocí LINQ to DataSet. Další informace najdete v tématu [LINQ to DataSet](../linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Pokyny pro aplikace, které vážou data s ovládacími prvky  
 .NET Framework umožňuje zapouzdřit data ve zdroji dat, jako je například datová sada nebo ovládací prvek zdroje dat ASP.NET, a následně navazovat prvky uživatelského rozhraní na tyto datové ovládací prvky. Následující seznam popisuje, jak svázat ovládací prvky s Entity Frameworkmi daty.  
  
- Svázání dat s ovládacími prvky.  

  Při dotazování konceptuálního modelu Entity Framework vrátí data jako objekty, které jsou instance typů entit. Tyto objekty mohou být vázány přímo na ovládací prvky a tato vazba podporuje aktualizace. To znamená, že změny dat v ovládacím prvku, jako je například řádek v <xref:System.Windows.Forms.DataGridView>, se automaticky uloží do databáze při volání metody <xref:System.Data.Objects.ObjectContext.SaveChanges%2A>.  
  
  Pokud vaše aplikace vytvoří výčet výsledků dotazu, aby zobrazila data v <xref:System.Windows.Forms.DataGridView> nebo jiném typu ovládacího prvku, který podporuje datovou vazbu, můžete upravit aplikaci tak, aby provedla vazbu ovládacího prvku s výsledkem <xref:System.Data.Objects.ObjectQuery%601>.  
  
  Další informace naleznete v tématu [vázání objektů k ovládacím prvkům](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100)).  
  
- Ovládací prvky zdroje dat ASP.NET.  

  Entity Framework obsahuje ovládací prvek zdroje dat navržený tak, aby zjednodušil datové vazby v ASP.NET webových aplikacích. Další informace najdete v tématu [Přehled ovládacího prvku webový server EntityDataSource](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100)).  
  
## <a name="other-considerations"></a>Ostatní úvahy  
 Níže jsou uvedeny předpoklady, které mohou být uplatněny při migraci konkrétních typů aplikací na Entity Framework.  
  
- Aplikace, které zveřejňují datové služby.  

  Webové služby a aplikace, které jsou založeny na Windows Communication Foundation (WCF) zveřejňují data z podkladového zdroje dat pomocí formátu zasílání zpráv požadavku a odpovědí XML. Entity Framework podporuje serializaci objektů entit pomocí binární, XML nebo serializace kontraktu dat WCF. Binární a serializace WCF podporují úplnou serializaci grafů objektů. Další informace najdete v tématu [vytváření N-vrstvých aplikací](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100)).  
  
- Aplikace, které používají data XML.  

  Serializace objektů umožňuje vytvářet Entity Framework datové služby. Tyto služby poskytují data aplikacím, které využívají data XML, jako jsou například internetové aplikace založené na AJAX. V těchto případech zvažte použití WCF Data Services. Tyto datové služby jsou založené na model EDM (Entity Data Model) a poskytují dynamický přístup k datům entit pomocí akcí protokolu HTTP Standard representational state transfer (REST), jako například GET, PUT a POST. Další informace najdete v tématu [WCF Data Services 4,5](../../wcf/index.md).  
  
  Entity Framework nepodporuje datový typ native-XML. To znamená, že když je entita namapována na tabulku se sloupcem XML, je ekvivalentní vlastnost entity pro sloupec XML řetězec. Objekty mohou být odpojeny a serializovány jako XML. Další informace naleznete v tématu [serializace objektů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
  Pokud vaše aplikace vyžaduje možnost dotazování na data XML, můžete i nadále využít výhod dotazů LINQ pomocí LINQ to XML. Další informace najdete v tématu [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) nebo [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
- Aplikace, které udržují stav.  

  Webové aplikace ASP.NET musí často udržovat stav webové stránky nebo uživatelské relace. Objekty v instanci <xref:System.Data.Objects.ObjectContext> lze uložit ve stavu zobrazení klienta nebo ve stavu relace na serveru a později načíst a znovu připojit k novému kontextu objektu. Další informace najdete v tématu [připojení a odpojení objektů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o nasazení](deployment-considerations.md)
- [Terminologie Entity Framework](terminology.md)
