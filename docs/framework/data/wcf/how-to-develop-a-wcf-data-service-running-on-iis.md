---
title: 'Postupy: Vývoj datové služby WCF ve službě IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 8a1a0c2c55267940463e2c9ab82bb52345269260
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121604"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Postup: Vývoj datové služby WCF spuštěné ve službě IIS

Tento článek ukazuje, jak pomocí služby WCF Data Services vytvořit datovou službu založenou na ukázkové databázi Northwind, která je hostovaná ASP.NET webovou aplikaci spuštěnou v Internetové informační službě (IIS). Příklad, jak vytvořit stejnou datovou službu Northwind jako ASP.NET webovou aplikaci, která běží na ASP.NET vývojovém serveru, naleznete v [rychlém startu služby WCF Data Services](quickstart-wcf-data-services.md).

> [!NOTE]
> Chcete-li vytvořit datovou službu Northwind, nejprve nainstalujte ukázkovou databázi Northwind do místního počítače. Chcete-li databázi nainstalovat, spusťte skript Transact-SQL z [ukázkových databází Northwind a pubs pro microsoft sql server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).

Tento článek ukazuje, jak vytvořit datovou službu pomocí zprostředkovatele Entity Framework. K dispozici jsou i další poskytovatelé datových služeb. Další informace naleznete v tématu [Poskytovatelé datových služeb](data-services-providers-wcf-data-services.md).

Po vytvoření služby je nutné explicitně poskytnout přístup k prostředkům datové služby. Další informace naleznete v [tématu How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>Vytvoření ASP.NET webové aplikace spuštěné ve službě IIS

1. V sadě Visual Studio vyberte v nabídce **Soubor** **položku Nový** > **projekt**.

2. V dialogovém okně **Nový projekt** vyberte > **kategorii Web** **nainstalované** > [**Visual C#** nebo **Visual Basic].**

3. Vyberte šablonu **webové aplikace ASP.NET.**

4. Zadejte `NorthwindService` jako název projektu.

5. Klikněte na tlačítko **OK**.

6. V nabídce **Project** vyberte **možnost NorthwindService Properties**.

7. Vyberte kartu **Web** a potom vyberte **Použít místní webový server služby IIS**.

8. Klepněte na tlačítko **Vytvořit virtuální adresář** a potom klepněte na tlačítko **OK**.

9. Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operačním systému):

    - 32bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - 64bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     Tím zajistíte, že windows communication foundation (WCF) je registrována v počítači.

10. Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operačním systému):

    - 32bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - 64bitové systémy:

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     Tím zajistíte, že iis běží správně po wcf byl nainstalován v počítači. Bude pravděpodobně nutné restartovat službu IIS.

11. Při spuštění ASP.NET aplikace v systému IIS7 je nutné provést také následující kroky:

    1. Otevřete Správce služby IIS a přejděte do aplikace PhotoService v části **Výchozí web**.

    2. V **zobrazení funkcí**poklepejte na **položku Ověřování**.

    3. Na stránce **Ověřování** vyberte **možnost Anonymní ověřování**.

    4. V podokně **Akce** klikněte na **Upravit** a nastavte zaregistrovaný objekt zabezpečení, pod kterým se anonymní uživatelé připojí k webu.

    5. V dialogovém okně **Upravit anonymní ověřovací pověření** vyberte **identitu fondu aplikací**.

    > [!IMPORTANT]
    > Používáte-li účet síťové služby, udělíte anonymním uživatelům veškerý interní přístup k síti přidružený k tomuto účtu.

12. Pomocí SQL Server Management Studio, sqlcmd.exe nástroj nebo Transact-SQL Editor v sadě Visual Studio, spusťte následující příkaz Transact-SQL proti instanci SQL Server, který má připojenou databázi Northwind:

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    Tím se vytvoří přihlášení v instanci serveru SQL Server pro účet systému Windows používaný ke spuštění služby IIS. To umožňuje službě IIS připojit se k instanci serveru SQL Server.

13. S připojenou databází Northwind proveďte následující příkazy Transact-SQL:

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

    To uděluje práva na nové přihlášení, které umožňuje službě IIS číst data z databáze Northwind a zapisovat je.

## <a name="define-the-data-model"></a>Definování datového modelu

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu ASP.NET a potom klikněte na **přidat** > **novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte **ADO.NET datový model entity**.

3. Pro název datového modelu `Northwind.edmx`zadejte .

4. V Průvodci datovým modelem entity vyberte **Generovat z databáze**a klepněte na tlačítko **Další**.

5. Připojte datový model k databázi jedním z následujících kroků a potom klepněte na tlačítko **Další**:

    - Pokud již nemáte nakonfigurované připojení k databázi, klepněte na tlačítko **Nové připojení** a vytvořte nové připojení. Další informace naleznete v [tématu How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). Tato instance serveru SQL Server musí mít připojenu ukázkovou databázi Northwind.

         \-nebo -

    - Pokud máte již nakonfigurované připojení k databázi Northwind, vyberte toto připojení ze seznamu připojení.

6. Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políček pro zobrazení a uložené procedury.

7. Chcete-li průvodce zavřít, klepněte na tlačítko **Dokončit.**

## <a name="create-the-data-service"></a>Vytvoření datové služby

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu ASP.NET a potom klikněte na **přidat** > **novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte **datovou službu WCF**.

   ![Šablona položky datové služby WCF v Sadě Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Šablona **WCF Data Service** je k dispozici ve Visual Studiu 2015, ale ne v Visual Studiu 2017 nebo novějším.

3. Pro název služby zadejte `Northwind`.

     Visual Studio vytvoří xml značky a soubory kódu pro novou službu. Ve výchozím nastavení se otevře okno editoru kódu. V **Průzkumníku řešení**má služba název Northwind a rozšíření .svc.cs nebo .svc.vb.

4. V kódu datové služby nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje datovou službu typem, který je `NorthwindEntities`kontejnerem entity datového modelu, což je v tomto případě . Definice třídy by měla vypadat takto:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Viz také

- [Vystavení dat jako služby](exposing-your-data-as-a-service-wcf-data-services.md)
