---
title: 'Postupy: vytvoření datové služby pomocí LINQ to SQLho zdroje dat (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: cde5b9903a1fd164ce106a6a408ac4bb79976642
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802282"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Postupy: vytvoření datové služby pomocí LINQ to SQLho zdroje dat (WCF Data Services)

WCF Data Services zpřístupňuje data entit jako datovou službu. Zprostředkovatel reflexe umožňuje definovat datový model, který je založen na jakékoli třídě, která zpřístupňuje členy, které vracejí <xref:System.Linq.IQueryable%601> implementaci. Aby bylo možné provádět aktualizace dat ve zdroji dat, musí tyto třídy implementovat také rozhraní <xref:System.Data.Services.IUpdatable>. Další informace najdete v tématu [poskytovatelé Data Services](data-services-providers-wcf-data-services.md). V tomto tématu se dozvíte, jak vytvořit LINQ to SQL třídy, které přistupují k ukázkové databázi Northwind pomocí poskytovatele reflexe a jak vytvořit datovou službu založenou na těchto třídách dat.

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>Přidání tříd LINQ to SQL do projektu

1. V rámci Visual Basic C# nebo aplikace klikněte v nabídce **projekt** na položku **Přidat** > **novou položku**.

2. Klikněte na šablonu **třídy LINQ to SQL** .

3. Změňte název na **Northwind. dbml**.

4. Klikněte na tlačítko **Add** (Přidat).

     Soubor Northwind. dbml se přidá do projektu a otevře se Návrhář relací objektů (Návrhář O/R).

5. V Průzkumníku **serveru**/**Database**v části Northwind rozbalte **tabulky** a přetáhněte `Customers` tabulku do Návrhář relací objektů (O/R Designer).

     Třída entity `Customer` se vytvoří a zobrazí se na návrhové ploše.

6. Opakujte krok 6 pro tabulky `Orders`, `Order_Details`a `Products`.

7. Pravým tlačítkem myši klikněte na nový soubor. dbml, který představuje třídy LINQ to SQL a klikněte na **Zobrazit kód**.

     Tím se vytvoří nová stránka s kódem na pozadí s názvem Northwind.cs, která obsahuje definici částečné třídy pro třídu, která dědí z třídy <xref:System.Data.Linq.DataContext>, která v tomto případě je `NorthwindDataContext`.

8. Obsah souboru kódu Northwind.cs nahraďte následujícím kódem. Tento kód implementuje poskytovatele reflexe rozšířením <xref:System.Data.Linq.DataContext> a datových tříd vygenerovaných LINQ to SQL:

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Vytvoření datové služby pomocí datového modelu založeného na LINQ to SQL

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu ASP.NET a potom klikněte na **Přidat** > **Nová položka**.

2. V dialogovém okně **Přidat novou položku** vyberte šablonu **WCF Data Service** z kategorie **Web** .

   ![Šablona položky datové služby WCF v aplikaci Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Šablona **WCF Data Service** je k dispozici v aplikaci visual Studio 2015, ale ne v aplikaci visual Studio 2017 nebo novější.

3. Zadejte název služby a klikněte na tlačítko **OK**.

     Visual Studio vytvoří kód XML a soubory kódu pro novou službu. Ve výchozím nastavení se otevře okno Editor kódu.

4. V kódu pro datovou službu nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy definující datovou službu s typem, který je kontejnerem entit datového modelu, který je v tomto případě `NorthwindDataContext`.

5. V kódu pro datovou službu nahraďte zástupný kód ve funkci `InitializeService` následujícím způsobem:

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     To umožňuje autorizovaným klientům získat přístup k prostředkům pro tři zadané sady entit.

6. Chcete-li otestovat datovou službu Northwind. svc pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístup ke službě z webového prohlížeče](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření datové služby pomocí zdroje dat ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe](create-a-data-service-using-rp-wcf-data-services.md)
- [Zprostředkovatelé datových služeb](data-services-providers-wcf-data-services.md)
