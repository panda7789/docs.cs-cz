---
title: 'Postupy: Vytvoření datové služby pomocí LINQ to SQL zdroje dat (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 6489e451f3790e38ea821104fd2aca5a8c091ba6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053004"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Postupy: Vytvoření datové služby pomocí LINQ to SQL zdroje dat (WCF Data Services)

WCF Data Services zpřístupňuje data entit jako datovou službu. Zprostředkovatel reflexe umožňuje definovat datový model, který je založen na jakékoli třídě, která zpřístupňuje členy, které <xref:System.Linq.IQueryable%601> vracejí implementaci. Aby bylo možné provádět aktualizace dat ve zdroji dat, musí tyto třídy implementovat <xref:System.Data.Services.IUpdatable> také rozhraní. Další informace najdete v tématu [poskytovatelé Data Services](data-services-providers-wcf-data-services.md). V tomto tématu se dozvíte, jak vytvořit LINQ to SQL třídy, které přistupují k ukázkové databázi Northwind pomocí poskytovatele reflexe a jak vytvořit datovou službu založenou na těchto třídách dat.

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>Přidání tříd LINQ to SQL do projektu

1. V rámci Visual Basic nebo C# aplikace klikněte v nabídce **projekt** na příkaz **Přidat** > **novou položku**.

2. Klikněte na šablonu **třídy LINQ to SQL** .

3. Změňte název na **Northwind. dbml**.

4. Klikněte na **Přidat**.

     Soubor Northwind. dbml se přidá do projektu a otevře se Návrhář relací objektů (Návrhář O/R).

5. V Průzkumníku **serveru**/**databáze**v části Northwind rozbalte **tabulky** a přetáhněte `Customers` tabulku na Návrhář relací objektů (Návrhář O/R).

     Vytvoří se Třída entity, která se zobrazí na návrhové ploše. `Customer`

6. Opakujte krok 6 pro `Orders`tabulky, `Order_Details`a. `Products`

7. Pravým tlačítkem myši klikněte na nový soubor. dbml, který představuje třídy LINQ to SQL a klikněte na **Zobrazit kód**.

     Tím se vytvoří nová stránka s kódem na pozadí s názvem Northwind.cs, která obsahuje definici částečné třídy pro třídu, která dědí <xref:System.Data.Linq.DataContext> z třídy, která je `NorthwindDataContext`v tomto případě.

8. Obsah souboru kódu Northwind.cs nahraďte následujícím kódem. Tento kód implementuje poskytovatele reflexe rozšířením <xref:System.Data.Linq.DataContext> tříd a datových tříd vygenerovaných LINQ to SQL:

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Vytvoření datové služby pomocí datového modelu založeného na LINQ to SQL

1. V **Průzkumník řešení**klikněte pravým tlačítkem na název projektu ASP.NET a pak klikněte na **Přidat** > **novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte šablonu **WCF Data Service** z kategorie **Web** .

   ![Šablona položky datové služby WCF v aplikaci Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Šablona **WCF Data Service** je k dispozici v aplikaci visual Studio 2015, ale ne v aplikaci visual Studio 2017.

3. Zadejte název služby a klikněte na tlačítko **OK**.

     Visual Studio vytvoří kód XML a soubory kódu pro novou službu. Ve výchozím nastavení se otevře okno Editor kódu.

4. V kódu pro datovou službu nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy definující datovou službu typem, který je kontejnerem entit datového modelu, který je v tomto `NorthwindDataContext`případě.

5. V kódu pro datovou službu nahraďte zástupný kód ve `InitializeService` funkci následujícím textem:

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     To umožňuje autorizovaným klientům získat přístup k prostředkům pro tři zadané sady entit.

6. Chcete-li otestovat datovou službu Northwind. svc pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístup ke službě z webového prohlížeče](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření datové služby pomocí zdroje dat Entity Framework ADO.NET](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Postupy: Vytvoření datové služby pomocí zprostředkovatele reflexe](create-a-data-service-using-rp-wcf-data-services.md)
- [Zprostředkovatelé datových služeb](data-services-providers-wcf-data-services.md)
