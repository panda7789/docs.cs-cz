---
title: N-vrstvé nastavení LINQ to SQL s webovými službami
ms.date: 03/30/2017
ms.assetid: 9cb10eb8-957f-4beb-a271-5f682016fed2
ms.openlocfilehash: 7b13a0cd77925423a12c093b1b5ac9b63ad7e019
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107403"
---
# <a name="linq-to-sql-n-tier-with-web-services"></a>N-vrstvé nastavení LINQ to SQL s webovými službami
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je navržená speciálně pro použití ve střední vrstvě. v vrstvy přístupu k datům volně spárované (DAL), jako jsou webové služby. Pokud prezentační vrstvy je webová stránka ASP.NET, pak můžete použít <xref:System.Web.UI.WebControls.LinqDataSource> ovládacího prvku webového serveru pro správu přenosu dat mezi uživatelského rozhraní a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] na střední vrstvě. Pokud prezentační vrstva není stránky ASP.NET, pak střední vrstvy a prezentační vrstvou musí provést další úkony ke správě serializace a deserializace dat.  
  
## <a name="setting-up-linq-to-sql-on-the-middle-tier"></a>Nastavení technologie LINQ to SQL ve střední vrstvě.  
 Ve webové služby nebo n vrstvá aplikace střední vrstvy obsahuje kontext dat a tříd entit. Tyto třídy můžete vytvořit ručně nebo pomocí obou SQLMetal.exe nebo [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] jako jinde popsaných v dokumentaci. V době návrhu máte možnost provést serializovatelné třídy entit. Další informace najdete v tématu [jak: Nastavení entit jako serializovatelných](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md). Další možností je vytvořit samostatnou sadu tříd, které provádí zapouzdření data, která mají být serializován a potom projekt do těchto Serializovatelné typy po vrácení dat ve vaší [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazy.  
  
 Potom definujte rozhraní s metodami, které klienti budou volat pro načtení, vložení a aktualizovat data. Metody rozhraní zabalit vaše [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazy. Pro zpracování volání vzdálené metody a serializace dat můžete použít jakýkoli druh mechanismu serializace. Jediným požadavkem je, že pokud máte cyklické nebo obousměrné relace v objektovém modelu, jako je například, že mezi zákazníci a objednávky v objektovém modelu standardní Northwind pak musíte použít serializátor, která ho podporuje. Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> podporuje obousměrné relace, ale XmlSerializer, který se používá s WCF Web services nepodporuje. Pokud vyberete použití XmlSerializer, pak musí zajistíte, že objektový model nemá žádné cyklické relace.  
  
 Další informace o Windows Communication Foundation, najdete v části [služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio).  
  
 Implementovat obchodních pravidel nebo další logiku domény pomocí částečné třídy a metody na <xref:System.Data.Linq.DataContext> a tříd entit k připojení do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] běhové události. Další informace najdete v tématu [implementace N-vrstvé obchodní logiky](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md).  
  
## <a name="defining-the-serializable-types"></a>Definování Serializovatelné typy  
 Na úrovni klienta nebo prezentace musí mít definice typu pro třídy, které se budou přijímat od střední vrstvy. Mohou být tyto typy tříd entit sami nebo speciální třídy, které balí pouze určitá pole ze tříd entit pro vzdálenou komunikaci. V každém případě [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je zcela unconcerned o jak prezentační vrstvy získá tyto definice typu. Například prezentační vrstvou může pomocí WCF generovat typy automaticky, nebo to může mít kopii knihovny DLL, ve kterém jsou tyto typy definice nebo ji stačí definovat vlastní verze typů.  
  
## <a name="retrieving-and-inserting-data"></a>Načítání a vkládání dat  
 Střední vrstva definuje rozhraní, která určuje, jak prezentační vrstvy přistupuje k datům. Například `GetProductByID(int productID)`, nebo `GetCustomers()`. Ve střední vrstvě tělo metody obvykle vytvoří novou instanci třídy <xref:System.Data.Linq.DataContext>, provede dotaz na jeden nebo více jeho tabulek. Střední vrstva pak vrátí výsledek jako <xref:System.Collections.Generic.IEnumerable%601>, kde `T` třídu entity nebo jiný typ, který je použitý pro serializaci. Prezentační vrstva nikdy odesílá nebo přijímá proměnné dotazu přímo do nebo z střední vrstvy. Dvě úrovně exchange hodnoty, objekty a kolekce konkrétní data. Poté, co přijal kolekci, můžete použít prezentační vrstvy [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] na objekty v případě potřeby ji dotazovat.  
  
 Při vkládání dat, můžete vytvořit nový objekt a jeho odeslání do střední vrstvy prezentační vrstvy, nebo můžete mít střední vrstvy vytvoření objektu podle hodnoty, které poskytuje. Obecně platí načtení a vložení dat do n vrstvé aplikace liší mnohem z procesu na 2vrstvých aplikací. Další informace najdete v tématu [dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md) a [vytváření a odesílání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md).  
  
## <a name="tracking-changes-for-updates-and-deletes"></a>Sledování změn pro aktualizace a odstranění  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje optimistické řízení souběžnosti na základě časových razítek (nazývaná také RowVersions) a na původní hodnoty. Pokud databázových tabulek mají časové razítko, bude aktualizace a odstranění vyžadovat trochu práce navíc na střední vrstvy nebo prezentační vrstvy. Ale pokud je nutné použít původní hodnoty pro kontroly optimistického řízení souběžnosti, pak prezentační vrstva zodpovídá za sledování tyto hodnoty a jejich odeslání zpět při zpřístupňuje aktualizace. Je to proto nebudou ve střední vrstvě pro účely změny, které byly provedeny u entit v prezentační vrstvě. Ve skutečnosti původní načtení entity a konečný výsledek aktualizace provedené obvykle provádí dvě zcela samostatné instance <xref:System.Data.Linq.DataContext>.  
  
 Větší počet změn, které provádí prezentační vrstva, tím složitější bude sledovat tyto změny a balíček, který je zase do střední vrstvy. Provádění mechanismus pro komunikaci změn je zcela na aplikaci. Jediným požadavkem je, že [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musí předávat původní hodnoty, které jsou požadovány kontroly optimistické souběžnosti.  
  
 Další informace najdete v tématu [CUD operace v N-vrstvé aplikace (LINQ to SQL) a načítání dat](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).  
  
## <a name="see-also"></a>Viz také:

- [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [Přehled ovládacího prvku zdroje dat LinqDataSource webového serveru](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))
