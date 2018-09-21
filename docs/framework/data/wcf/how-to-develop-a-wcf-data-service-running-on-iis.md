---
title: 'Postupy: vývoj datové služby WCF ve službě IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: af81e65dfd4661d62d7aa4a3e6075be312765cb7
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46482076"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Postupy: vývoj datové služby WCF ve službě IIS

Toto téma ukazuje, jak pomocí služeb WCF Data Services k vytvoření datové služby, který je založen na ukázkové databáze Northwind, která je hostována ve webové aplikaci ASP.NET, na kterém běží v Internetové informační služby (IIS). Příklad toho, jak vytvořit stejný datová služba Northwind jako webovou aplikaci ASP.NET, která běží na serveru ASP.NET Development Server, najdete v článku [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).

> [!NOTE]
> Pokud chcete vytvořit datová služba Northwind, jste na místním počítači nainstalovali ukázkové databáze Northwind. Stáhněte si tuto ukázkovou databázi, naleznete na stránce stahování [ukázkové databáze systému SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).

 Toto téma ukazuje, jak vytvořit datové služby pomocí zprostředkovatele Entity Framework. Ostatní zprostředkovatelé dat služby jsou k dispozici. Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).

 Po vytvoření služby, je nutné explicitně zadat přístup k prostředkům datové služby. Další informace najdete v tématu [postupy: povolení přístup k datové službě](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>Vytvoření webové aplikace ASP.NET, která běží ve službě IIS

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. V **nový projekt** dialogové okno, vyberte **nainstalováno** > [**Visual C#** nebo **jazyka Visual Basic**] > **webové** kategorie.

3. Vyberte **webová aplikace ASP.NET** šablony.

1. Zadejte `NorthwindService` jako název projektu.

5. Klikněte na tlačítko **OK**.

6. Na **projektu** nabídce vyberte možnost **NorthwindService vlastnosti**.

7. Vyberte **webové** kartu a potom vyberte **použití místní webový Server IIS**.

8. Klikněte na tlačítko **vytvořit virtuální adresář** a potom klikněte na tlačítko **OK**.

9. Z příkazového řádku s oprávněními správce proveďte jednu z následujících příkazů (v závislosti na operačním systému):

    -   32bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    -   64bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     Tím zajistíte, že je v počítači registrována Windows Communication Foundation (WCF).

10. Z příkazového řádku s oprávněními správce proveďte jednu z následujících příkazů (v závislosti na operačním systému):

    -   32bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    -   64bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     Tím je zajištěno, že služba IIS běží správně po instalaci WCF v počítači. Budete muset také restartovat službu IIS.

11. Když je spuštěná aplikace ASP.NET ve službě IIS7, je třeba provést následující kroky:

    1. Otevřete Správce služby IIS a přejděte do aplikace PhotoService v rámci **výchozí webový server**.

    2. V **zobrazení funkcí**, dvakrát klikněte na panel **ověřování**.

    3. Na **ověřování** stránce **anonymní ověřování**.

    4. V **akce** podokně klikněte na tlačítko **upravit** nastavení zabezpečení objektu zabezpečení, pod které anonymní uživatele se připojí k lokalitě.

    5. V **upravit pověření anonymního ověřování** dialogu **identita fondu aplikací**.

    > [!IMPORTANT]
    > Pokud používáte účet Network Service, udělíte anonymním uživatelům všechna přístup k interní síti přidružené k tomuto účtu.

12. Pomocí SQL Server Management Studio, nástroje sqlcmd.exe nebo editoru jazyka Transact-SQL v sadě Visual Studio, spusťte následující příkaz jazyka Transact-SQL pro instanci systému SQL Server, který má připojené databázi Northwind:

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    Tím se vytvoří přihlášení v instanci systému SQL Server pro účet Windows použitý ke spuštění služby IIS. To umožňuje službě IIS pro připojení k instanci systému SQL Server.

13. S databází Northwind, připojit spusťte následující příkazy jazyka Transact-SQL:

    ```sql
    USE Northwind
    GO
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];
    GO
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]
    WITH DEFAULT_DATABASE=[Northwind];
    GO
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    ```

    Tím udělíte práva k nové přihlašovací údaje, které umožňuje službě IIS čtení dat z a zapisovat data do databáze Northwind.

## <a name="define-the-data-model"></a>Definování datového modelu

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu technologie ASP.NET a potom klikněte na tlačítko **přidat** > **nová položka**.

2. V **přidat novou položku** dialogu **datový Model Entity ADO.NET**.

3. Název datového modelu, zadejte `Northwind.edmx`.

4. V Průvodci modelem Entity Data vyberte **Generovat z databáze**a potom klikněte na tlačítko **Další**.

5. Datový model připojení k databázi pomocí jedné z následujících kroků a potom klikněte na tlačítko **Další**:

    -   Pokud nemáte připojení k databázi, která jsou už nakonfigurovaná, klikněte na tlačítko **nové připojení** a vytvořit nové připojení. Další informace najdete v tématu [postupy: vytvoření připojení k databázím SQL Server](https://go.microsoft.com/fwlink/?LinkId=123631). Tato instance systému SQL Server musí mít připojené ukázkové databáze Northwind.

         \- nebo –

    -   Pokud máte připojení k databázi již byla konfigurována pro připojení k databázi Northwind, vyberte v seznamu připojení toto připojení.

6. Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políček pro zobrazení a uložených procedur.

7. Klikněte na tlačítko **Dokončit** zavřete průvodce.

## <a name="create-the-data-service"></a>Vytvoření datové služby

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu ASP.NET a potom klikněte na **přidat** > **nová položka**.

2. V **přidat novou položku** dialogu **službu WCF Data Service**.

   ![Služby WCF Data Service šablony položky v sadě Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **Službu WCF Data Service** šablona je k dispozici v sadě Visual Studio 2015, ale ne v sadě Visual Studio 2017.

3. Název služby, zadejte `Northwind`.

     Visual Studio vytvoří soubory značek a kódu XML pro novou službu. Ve výchozím nastavení otevře se okno editoru kódu. V **Průzkumníka řešení**, služba má název, Northwind a rozšíření. svc.cs nebo. svc.vb.

4. V kódu pro datovou službu, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje datové služby s typem, který je kontejner entit datového modelu, který v tomto případě je `NorthwindEntities`. Definice třídy by měl vypadat to následující:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Viz také:

- [Vystavení dat jako služby](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
