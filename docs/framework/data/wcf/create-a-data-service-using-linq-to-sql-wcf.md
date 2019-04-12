---
title: 'Postupy: Vytvoření datové služby pomocí LINQ ke zdroji dat SQL (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: b33eb8f470fc8ce3851c7843de992b39e86ce018
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518217"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Postupy: Vytvoření datové služby pomocí LINQ ke zdroji dat SQL (WCF Data Services)

Služby WCF Data Services zpřístupňuje entity data jako datové služby. Zprostředkovatel reflexe umožňuje definovat datový model, který je založen na jakoukoli třídu, která zveřejňuje členy který vrací <xref:System.Linq.IQueryable%601> implementace. Aby bylo možné provést aktualizace dat ve zdroji dat, musíte také implementovat tyto třídy <xref:System.Data.Services.IUpdatable> rozhraní. Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md). Toto téma ukazuje, jak vytvořit LINQ na třídy SQL, které přístup k ukázkové databázi Northwind pomocí zprostředkovatel reflexe, jakož i jak vytvořit datovou službu, která je založena na těchto datových tříd.

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>Chcete-li přidat LINQ na třídy SQL do projektu

1. Z v rámci aplikace Visual Basic nebo C# na **projektu** nabídky, klikněte na tlačítko **přidat** > **nová položka**.

2. Klikněte na tlačítko **třídy LINQ to SQL** šablony.

3. Změňte název na **Northwind.dbml**.

4. Klikněte na **Přidat**.

     Do projektu se přidá soubor Northwind.dbml a otevře se Návrhář relací objektů (O/R Designer).

5. V **Server**/**Průzkumník databáze**, v části Northwind, rozbalte položku **tabulky** a přetáhněte ji `Customers` tabulky do Návrháře relací objektů (O/R Návrhář).

     A `Customer` třídy entita se vytvoří a zobrazí na návrhové ploše.

6. Opakujte krok 6 pro `Orders`, `Order_Details`, a `Products` tabulky.

7. Klikněte pravým tlačítkem na nový soubor .dbml, který představuje LINQ na třídy SQL a klikněte na **zobrazit kód**.

     Tím se vytvoří nová stránka použití modelu code-behind Northwind.cs, který obsahuje definici částečnou třídu, která dědí z třídy s názvem <xref:System.Data.Linq.DataContext> třídu, která v tomto případě je `NorthwindDataContext`.

8. Nahraďte obsah souboru Northwind.cs kód následujícím kódem. Tento kód implementuje zprostředkovatel reflexe tím, že rozšíří <xref:System.Data.Linq.DataContext> a datových tříd, které jsou generovány pomocí LINQ to SQL:

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Vytvoření datové služby pomocí LINQ to SQL na základě datového modelu

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu ASP.NET a potom klikněte na **přidat** > **nová položka**.

2. V **přidat novou položku** dialogové okno, vyberte **službu WCF Data Service** šablonu z **webové** kategorie.

   ![Služby WCF Data Service šablony položky v sadě Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **Službu WCF Data Service** šablona je k dispozici v sadě Visual Studio 2015, ale ne v sadě Visual Studio 2017.

3. Zadejte název pro službu a pak klikněte na tlačítko **OK**.

     Visual Studio vytvoří soubory značek a kódu XML pro novou službu. Ve výchozím nastavení otevře se okno editoru kódu.

4. V kódu pro datovou službu, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje datové služby s typem, který je kontejner entit datového modelu, který v tomto případě je `NorthwindDataContext`.

5. V kódu pro datovou službu, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     To umožňuje autorizovaným klientům přístup k prostředkům tři určené sady entit.

6. Pokud chcete testovat službu Northwind.svc dat pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístupu ke službě z webového prohlížeče](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření datové služby pomocí zdroje dat rozhraní ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)