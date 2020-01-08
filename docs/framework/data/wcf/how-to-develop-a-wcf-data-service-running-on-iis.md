---
title: 'Postupy: vývoj datové služby WCF běžící v rámci služby IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 5c75425783d3468ac42ef7cb32cd9c93e812192a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338340"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Postupy: vývoj datové služby WCF běžící v rámci služby IIS

V tomto tématu se dozvíte, jak pomocí WCF Data Services vytvořit datovou službu založenou na ukázkové databázi Northwind, jejímž hostitelem je webová aplikace ASP.NET, která běží na Internetová informační služba (IIS). Příklad toho, jak vytvořit stejnou datovou službu Northwind jako ASP.NET webovou aplikaci, která běží na vývojovém serveru ASP.NET, najdete v tématu [rychlý start WCF Data Services](quickstart-wcf-data-services.md).

> [!NOTE]
> Chcete-li vytvořit datovou službu Northwind, je nutné mít nainstalovanou ukázkovou databázi Northwind na místním počítači. Pokud si chcete stáhnout tuto ukázkovou databázi, přečtěte si část [databáze pro stahování a ukázkové databáze pro SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).

V tomto tématu se dozvíte, jak vytvořit datovou službu pomocí poskytovatele Entity Framework. Další poskytovatelé datových služeb jsou k dispozici. Další informace najdete v tématu [poskytovatelé Data Services](data-services-providers-wcf-data-services.md).

Po vytvoření služby je nutné výslovně poskytnout přístup k prostředkům datové služby. Další informace najdete v tématu [Postup: povolení přístupu k datové službě](how-to-enable-access-to-the-data-service-wcf-data-services.md).

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>Vytvoření webové aplikace v ASP.NET, která běží na službě IIS

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový** > **projekt**.

2. V dialogovém okně **Nový projekt** vyberte > **Webová** kategorie **instalované** > [**Visual C#**  nebo **Visual Basic**].

3. Vyberte šablonu **webové aplikace ASP.NET** .

4. Jako název projektu zadejte `NorthwindService`.

5. Klikněte na tlačítko **OK**.

6. V nabídce **projekt** vyberte **vlastnosti NorthwindService**.

7. Vyberte kartu **Web** a pak vyberte **použít místní webový server služby IIS**.

8. Klikněte na **vytvořit virtuální adresář** a pak klikněte na **OK**.

9. Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operačním systému):

    - 32bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - 64bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     Tím se zajistí, že se v počítači zaregistruje Windows Communication Foundation (WCF).

10. Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operačním systému):

    - 32bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - 64bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     Tím se zajistí, aby služba IIS běžela správně po instalaci WCF do počítače. Možná budete muset restartovat taky službu IIS.

11. Když je aplikace ASP.NET spuštěna v IIS7, je nutné provést také následující kroky:

    1. Otevřete Správce služby IIS a v části **výchozí webový server**přejděte na aplikaci inSlužba.

    2. V **zobrazení funkcí**poklikejte na **ověřování**.

    3. Na stránce **ověřování** vyberte **anonymní ověřování**.

    4. V podokně **Akce** klikněte na **Upravit** a nastavte objekt zabezpečení, pod kterým se budou anonymní uživatelé připojovat k webu.

    5. V dialogovém okně **Upravit pověření anonymního ověřování** vyberte možnost **identita fondu aplikací**.

    > [!IMPORTANT]
    > Když použijete účet síťové služby, udělíte anonymním uživatelům všechna přístupová práva k interní síti, která jsou přidružená k tomuto účtu.

12. Pomocí SQL Server Management Studio, nástroje Sqlcmd. exe nebo editoru Transact-SQL v aplikaci Visual Studio spusťte následující příkaz Transact-SQL pro instanci SQL Server s připojenou databází Northwind:

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    Tím se vytvoří přihlášení v instanci SQL Server pro účet systému Windows, který se používá ke spouštění služby IIS. To umožňuje službě IIS připojit se k instanci SQL Server.

13. S připojenou databází Northwind spusťte následující příkazy jazyka Transact-SQL:

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

    Tím se uděluje oprávnění k novému přihlášení, které službě IIS umožňuje číst data a zapisovat data do databáze Northwind.

## <a name="define-the-data-model"></a>Definování datového modelu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu ASP.NET a potom klikněte na **Přidat** > **Nová položka**.

2. V dialogovém okně **Přidat novou položku** vyberte **ADO.NET model EDM (Entity Data Model)** .

3. Pro název datového modelu zadejte `Northwind.edmx`.

4. V průvodci model EDM (Entity Data Model) vyberte **Generovat z databáze**a pak klikněte na **Další**.

5. Pomocí jednoho z následujících kroků připojte datový model k databázi a potom klikněte na tlačítko **Další**:

    - Pokud již nemáte nakonfigurované připojení k databázi, klikněte na tlačítko **nové připojení** a vytvořte nové připojení. Další informace naleznete v tématu [How to: Create Connections to SQL Server databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). Tato instance SQL Server musí mít připojenou ukázkovou databázi Northwind.

         \- nebo –

    - Pokud máte připojení k databázi, které je už nakonfigurované pro připojení k databázi Northwind, vyberte toto připojení ze seznamu připojení.

6. Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políček u zobrazení a uložených procedur.

7. Kliknutím na tlačítko **Dokončit** zavřete průvodce.

## <a name="create-the-data-service"></a>Vytvoření datové služby

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu ASP.NET a potom klikněte na **Přidat** > **Nová položka**.

2. V dialogovém okně **Přidat novou položku** vyberte **WCF Data Service**.

   ![Šablona položky datové služby WCF v aplikaci Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Šablona **WCF Data Service** je k dispozici v aplikaci visual Studio 2015, ale ne v aplikaci visual Studio 2017 nebo novější.

3. Jako název služby zadejte `Northwind`.

     Visual Studio vytvoří kód XML a soubory kódu pro novou službu. Ve výchozím nastavení se otevře okno Editor kódu. V **Průzkumník řešení**má služba název, Northwind a příponu. svc.cs nebo. svc. vb.

4. V kódu pro datovou službu nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy definující datovou službu s typem, který je kontejnerem entit datového modelu, který je v tomto případě `NorthwindEntities`. Definice třídy by měla vypadat takto:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Viz také:

- [Vystavení dat jako služby](exposing-your-data-as-a-service-wcf-data-services.md)
