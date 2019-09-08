---
title: Vytvoření datové služby WCF v aplikaci Visual Studio
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: c3c80fb48635199f45acb1e72bf756bbc65d2e14
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780407"
---
# <a name="create-the-data-service"></a>Vytvoření datové služby

V tomto tématu vytvoříte ukázkovou datovou službu, která používá WCF Data Services k vystavení [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu, který je založen na ukázkové databázi Northwind. Úkol zahrnuje následující základní kroky:

1. Vytvoření webové aplikace v ASP.NET

2. Definujte datový model pomocí model EDM (Entity Data Model)ch nástrojů.

3. Přidejte datovou službu do webové aplikace.

4. Povolte přístup k datové službě.

## <a name="create-the-aspnet-web-app"></a>Vytvoření webové aplikace v ASP.NET

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový** > **projekt**.

1. V dialogovém okně **Nový projekt** v části buď Visual Basic nebo Visual C# vyberte kategorii **Web** a pak vyberte **ASP.NET webová aplikace**.

1. Jako `NorthwindService` název projektu zadejte a pak vyberte **OK**.

1. V dialogovém okně **Nová webová aplikace ASP.NET** vyberte **prázdné** a pak vyberte **OK**.

1. Volitelné Zadejte konkrétní číslo portu pro vaši webovou aplikaci. Poznámka: číslo `12345` portu se používá v této řadě témat pro rychlý Start.

    1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt ASP.NET, který jste právě vytvořili, a pak zvolte **vlastnosti**.

    2. Vyberte kartu **Web** a nastavte hodnotu textového pole **konkrétní port** na `12345`.

## <a name="define-the-data-model"></a>Definování datového modelu

1. V **Průzkumník řešení**klikněte pravým tlačítkem na název projektu ASP.NET a pak klikněte na **Přidat** > **novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte kategorii **dat** a pak vyberte **ADO.NET model EDM (Entity Data Model)** .

3. Jako název datového modelu zadejte `Northwind.edmx`.

4. V **průvodci model EDM (Entity Data Model)** vyberte **EF Designer z databáze**a pak klikněte na **Další**.

5. Pomocí jednoho z následujících kroků připojte datový model k databázi a potom klikněte na tlačítko **Další**:

    - Pokud nemáte připojení databáze již nakonfigurováno, klikněte na tlačítko **nové připojení** a vytvořte nové připojení. Další informace najdete v tématu [jak: Umožňuje vytvořit připojení k SQL Server](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))databází. Tato instance SQL Server musí mít připojenou ukázkovou databázi Northwind.

         \- nebo –

    - Pokud máte připojení k databázi, které je už nakonfigurované pro připojení k databázi Northwind, vyberte toto připojení ze seznamu připojení.

6. Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políček u zobrazení a uložených procedur.

7. Kliknutím na tlačítko **Dokončit** zavřete průvodce.

## <a name="create-the-wcf-data-service"></a>Vytvoření datové služby WCF

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt ASP.NET a pak zvolte možnost **Přidat** > **novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte v kategorii **Web** šablonu položky **datové služby WCF** .

   ![Šablona položky datové služby WCF v aplikaci Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Šablona **WCF Data Service** je k dispozici v aplikaci visual Studio 2015, ale ne v aplikaci visual Studio 2017.

3. Jako název služby zadejte `Northwind`.

     Visual Studio vytvoří kód XML a soubory kódu pro novou službu. Ve výchozím nastavení se otevře okno Editor kódu. V **Průzkumník řešení**služba má název Northwind s příponou *. svc.cs* nebo *. svc. vb*.

4. V kódu pro datovou službu nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy definující datovou službu typem, který je kontejnerem entit datového modelu, který je v tomto `NorthwindEntities`případě. Definice třídy by měla vypadat takto:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a>Povolit přístup k prostředkům datové služby

1. V kódu pro datovou službu nahraďte zástupný kód ve `InitializeService` funkci následujícím textem:

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     To umožňuje autorizovaným klientům mít přístup pro čtení a zápis k prostředkům pro zadané sady entit.

    > [!NOTE]
    > Každý klient, který má přístup k aplikaci ASP.NET, může také přistupovat k prostředkům vystaveným datovou službou. V provozní datové službě, abyste zabránili neoprávněnému přístupu k prostředkům, měli byste také zabezpečit samotnou aplikaci. Další informace najdete v tématu [zabezpečení WCF Data Services](securing-wcf-data-services.md).

## <a name="next-steps"></a>Další postup

Úspěšně jste vytvořili novou datovou službu, která zveřejňuje kanál OData založený na ukázkové databázi Northwind a povolili jste přístup k informačnímu kanálu pro klienty, kteří mají oprávnění k webové aplikaci ASP.NET. V dalším kroku spustíte datovou službu ze sady Visual Studio a získáte přístup k datovému kanálu OData odesláním požadavků HTTP GET přes webový prohlížeč:

> [!div class="nextstepaction"]
> [Přístup ke službě z webového prohlížeče](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Viz také:

- [ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
