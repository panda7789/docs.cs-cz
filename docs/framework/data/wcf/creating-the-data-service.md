---
title: Vytvoření datové služby WCF v sadě Visual Studio
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: e8d82ff8958af12842366911b6633ea6b2e0efbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765847"
---
# <a name="create-the-data-service"></a>Vytvoření datové služby

V tomto tématu vytvoříte ukázkové datových služeb WCF Data Services využívá k tomu, [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informační kanál, který je založen na ukázkovou databázi Northwind. Úloha zahrnuje následující základní kroky:

1. Vytvoření webové aplikace ASP.NET.

2. Definování datového modelu s použitím nástroje modelu Entity Data Model.

3. Přidáte datové služby na webovou aplikaci.

4. Povolení přístupu k datové službě.

## <a name="create-the-aspnet-web-app"></a>Vytvoření webové aplikace ASP.NET

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

1. V **nový projekt** dialogové okno, v rámci jazyka Visual Basic nebo Visual C# vyberte **webové** kategorie a pak vyberte **webová aplikace ASP.NET**.

1. Zadejte `NorthwindService` jako název projektu a pak vyberte **OK**.

1. V **nová webová aplikace ASP.NET** dialogového okna, vyberte **prázdný** a pak vyberte **OK**.

1. (Volitelné) Zadejte číslo portu specifické pro vaši webovou aplikaci. Poznámka: číslo portu `12345` slouží v této sérii témat rychlý start.

    1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt ASP.NET, který jste právě vytvořili a klikněte na tlačítko **vlastnosti**.

    2. Vyberte **webové** kartu a nastavte hodnotu **specifického portu** textové pole pro `12345`.

## <a name="define-the-data-model"></a>Definování datového modelu

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu technologie ASP.NET a potom klikněte na tlačítko **přidat** > **nová položka**.

2. V **přidat novou položku** dialogové okno, vyberte **Data** kategorie a pak vyberte **datový Model Entity ADO.NET**.

3. Název datového modelu, zadejte `Northwind.edmx`.

4. V **Průvodce datovým modelem Entity**vyberte **EF designeru z databáze**a potom klikněte na tlačítko **Další**.

5. Datový model připojení k databázi pomocí jedné z následujících kroků a potom klikněte na tlačítko **Další**:

    - Pokud nemáte připojení k databázi, která jsou už nakonfigurovaná, klikněte na tlačítko **nové připojení** a vytvořit nové připojení. Další informace najdete v tématu [jak: Vytvoření připojení k databázím serveru SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). Tato instance systému SQL Server musí mít připojené ukázkové databáze Northwind.

         \- nebo –

    - Pokud máte připojení k databázi již byla konfigurována pro připojení k databázi Northwind, vyberte v seznamu připojení toto připojení.

6. Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políček pro zobrazení a uložených procedur.

7. Klikněte na tlačítko **Dokončit** zavřete průvodce.

## <a name="create-the-wcf-data-service"></a>Vytvoření datové služby WCF

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt ASP.NET a klikněte na tlačítko **přidat** > **nová položka**.

2. V **přidat novou položku** dialogové okno, vyberte **službu WCF Data Service** šablony položky z **webové** kategorie.

   ![Služby WCF Data Service šablony položky v sadě Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **Službu WCF Data Service** šablona je k dispozici v sadě Visual Studio 2015, ale ne v sadě Visual Studio 2017.

3. Název služby zadáte `Northwind`.

     Visual Studio vytvoří soubory značek a kódu XML pro novou službu. Ve výchozím nastavení otevře se okno editoru kódu. V **Průzkumníka řešení**, službu s názvem Northwind s příponou *. svc.cs* nebo *. svc.vb*.

4. V kódu pro datovou službu, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje datové služby s typem, který je kontejner entit datového modelu, který v tomto případě je `NorthwindEntities`. Definice třídy by měl vypadat to následující:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a>Povolení přístupu k prostředkům datové služby

1. V kódu pro datovou službu, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     To umožňuje autorizovaným klientům ke čtení a zápis k prostředkům určené sady entit.

    > [!NOTE]
    > Libovolného klienta, který má přístup k aplikaci technologie ASP.NET můžete také přístup k prostředkům vystavené datové služby. V produkčním datové služby chcete-li zabránit neoprávněnému přístupu k prostředkům byste měli také zabezpečit samotná aplikace. Další informace najdete v tématu [zabezpečení služeb WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).

## <a name="next-steps"></a>Další kroky

Úspěšně jste vytvořili novou službu data, která vystavuje kanál OData, která je založena na ukázkovou databázi Northwind a povolíte přístup ke kanálu pro klienty, kteří mají oprávnění na webovou aplikaci ASP.NET. Teď se spustit službu data ze sady Visual Studio a přístup, odešlete požadavky HTTP GET přes webový prohlížeč datového kanálu OData:

> [!div class="nextstepaction"]
> [Přístup ke službě z webového prohlížeče](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Viz také:

- [Datový Model Entity ADO.NET nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))