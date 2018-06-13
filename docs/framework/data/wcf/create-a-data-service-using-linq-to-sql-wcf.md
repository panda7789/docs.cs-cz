---
title: 'Postupy: vytvoření služby dat pomocí LINQ ke zdroji dat SQL (služby WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 5769ff5296d096df41b59104ad0581f0e816c648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362244"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Postupy: vytvoření služby dat pomocí LINQ ke zdroji dat SQL (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zpřístupní entity data jako datové služby. Zprostředkovatel reflexe umožňuje definovat datového modelu, který je založena na všechny třídy, která zpřístupňuje členy, který vrací <xref:System.Linq.IQueryable%601> implementace. Abyste mohli provést aktualizace dat ve zdroji dat, musíte také implementovat tyto třídy <xref:System.Data.Services.IUpdatable> rozhraní. Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md). Toto téma ukazuje, jak vytvořit LINQ na SQL třídy, která přistupují k ukázková databáze Northwind pomocí reflexe poskytovatele, jakož i služba dat, která je založena na těchto třídách data vytvoření.  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a>Přidat do třídy SQL do projektu LINQ  
  
1.  Z v rámci aplikace Visual Basic a C#, na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
2.  Klikněte **třídy LINQ to SQL** šablony.  
  
3.  Změňte název **Northwind.dbml**.  
  
4.  Klikněte na tlačítko **přidat**.  
  
     Soubor Northwind.dbml je přidán do projektu a otevře Návrhář relací objektů (Návrhář relací objektů).  
  
5.  V **Server**/**Průzkumník databáze**, v části Northwind, rozbalte položku **tabulky** a přetáhněte ji `Customers` tabulky do Návrhář relací objektů (relací objektů Návrhář).  
  
     A `Customer` třídy entita se vytvoří a zobrazí se na návrhovou plochu.  
  
6.  Opakujte krok 6 pro `Orders`, `Order_Details`, a `Products` tabulky.  
  
7.  Klikněte pravým tlačítkem na nový soubor DBML, který představuje LINQ třídy SQL, klikněte na **kód zobrazení**.  
  
     Tím se vytvoří nová stránka kódu s názvem Northwind.cs, který obsahuje třídu definice pro třídu, která dědí z <xref:System.Data.Linq.DataContext> třída, která v tomto případě je `NorthwindDataContext`.  
  
8.  Obsah souboru Northwind.cs kódu nahraďte následujícím kódem. Tento kód implementuje zprostředkovatele reflexe tím, že rozšíří <xref:System.Data.Linq.DataContext> a datových tříd, které jsou generované technologie LINQ to SQL:  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Vytvoření služby dat pomocí LINQ to SQL na základě datového modelu  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název projektu ASP.NET a pak klikněte na tlačítko **přidat novou položku**.  
  
2.  V **přidat novou položku** dialogové okno, vyberte **služby WCF Data Service**.  
  
3.  Zadejte název pro službu a pak klikněte na tlačítko **OK**.  
  
     Visual Studio vytvoří soubory značek a kódu XML pro novou službu. Ve výchozím nastavení otevře se okno editoru kódu.  
  
4.  V kódu pro službu data, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje službu data s typem, který je kontejneru entit datového modelu, který v tomto případě je `NorthwindDataContext`.  
  
5.  V kódu pro službu data, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     To umožňuje autorizovaným klientům přístup k prostředkům pro tři sady zadané entity.  
  
6.  Chcete-li otestovat službu Northwind.svc data pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístupu ke službě z webového prohlížeče](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření datové služby pomocí zdroje dat ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
