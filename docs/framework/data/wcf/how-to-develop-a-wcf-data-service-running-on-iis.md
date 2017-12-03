---
title: "Postupy: vývoj WCF Data Service spuštěna ve službě IIS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 467c572d456bf2beca9f69359d362867aefbe5a1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Postupy: vývoj WCF Data Service spuštěna ve službě IIS
Toto téma ukazuje, jak používat [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] k vytvoření služby data, která je založena na ukázková databáze Northwind, který je hostitelem aplikace technologie ASP.NET, která běží na Internetové informační služby (IIS). Příklad vytvoření stejnou službu data Northwind jako aplikace technologie ASP.NET, která běží na vývojový Server ASP.NET naleznete v části [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
> [!NOTE]
>  Pokud chcete vytvořit službu Northwind data, musíte instalaci ukázková databáze Northwind v místním počítači. Stažení této ukázkové databáze, najdete v článku stránce pro stažení [ukázkové databáze systému SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).  
  
 Toto téma ukazuje, jak vytvořit službu dat pomocí zprostředkovatele Entity Framework. Jiných poskytovatelů služeb dat jsou k dispozici. Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
 Po vytvoření služby, je nutné explicitně zadat přístup k datovým prostředkům služby. Další informace najdete v tématu [postup: Povolit přístup ke službě Data](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a>Chcete-li vytvořit aplikaci ASP.NET, který běží ve službě IIS  
  
1.  V sadě Visual Studio na **soubor** nabídce vyberte možnost **nový**a potom vyberte **projektu**.  
  
2.  V **nový projekt** dialogovém okně vyberte jako programovací jazyk Visual Basic a Visual C#.  
  
3.  V **šablony** podokně, vyberte **webové aplikace ASP.NET**. Poznámka: Pokud používáte Visual Studio Web Developer, musíte vytvořit nový web místo novou webovou aplikaci.  
  
4.  Typ `NorthwindService` jako název projektu.  
  
5.  Click **OK**.  
  
6.  Na **projektu** nabídce vyberte možnost **NorthwindService vlastnosti**.  
  
7.  Vyberte **webové** a pak vyberte **použití místního webového serveru IIS**.  
  
8.  Klikněte na tlačítko **vytvořit virtuální adresář** a pak klikněte na **OK**.  
  
9. Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operační systém):  
  
    -   32bitové systémy:  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   64bitové systémy:  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     Tím je zajištěno, že Windows Communication Foundation (WCF) je zaregistrován v počítači.  
  
10. Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operační systém):  
  
    -   32bitové systémy:  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   64bitové systémy:  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     Tím je zajištěno, že služba IIS běží správně po instalaci WCF v počítači. Může mít také restartovat službu IIS.  
  
11. Když je spuštěná aplikace ASP.NET ve službě IIS7, je třeba provést následující kroky:  
  
    1.  Otevřete Správce služby IIS a přejděte do aplikace PhotoService pod **Default Web Site**.  
  
    2.  V **zobrazení funkcí**, dvakrát klikněte na **ověřování**.  
  
    3.  Na **ověřování** vyberte **anonymní ověřování**.  
  
    4.  V **akce** podokně klikněte na tlačítko **upravit** nastavení zabezpečení hlavní, pod které anonymní uživatelé se budou připojovat k webu.  
  
    5.  V **upravit pověření anonymního ověřování** dialogové okno, vyberte **identita fondu aplikací**.  
  
    > [!IMPORTANT]
    >  Pokud používáte účet Network Service, udělíte anonymním uživatelům všechna přístupová práva interní síti přidružená tohoto účtu.  
  
12. Pomocí SQL Server Management Studio, pomocí nástroje sqlcmd.exe nebo editoru jazyka Transact-SQL v sadě Visual Studio, spusťte následující příkaz Transact-SQL pro instanci systému SQL Server, který má databáze Northwind připojené:  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     Tím se vytvoří přihlášení v instanci serveru SQL pro účet Windows použitý ke spuštění služby IIS. To umožňuje službě IIS pro připojení k instanci systému SQL Server.  
  
13. S připojit databázi Northwind spusťte následující příkazy jazyka Transact-SQL:  
  
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
  
     Tím udělíte oprávnění k nové přihlašovací údaje, které umožňuje službě IIS ke čtení dat z a zapisovat data do databáze Northwind.  
  
### <a name="to-define-the-data-model"></a>Chcete-li definovat datový model  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název projektu ASP.NET a pak klikněte na tlačítko **přidat novou položku.**  
  
2.  V **přidat novou položku** dialogové okno, vyberte **ADO.NET Entity Data Model**.  
  
3.  Zadejte název datového modelu, `Northwind.edmx`.  
  
4.  V průvodci Entity Data Model vyberte **generování z databáze**a potom klikněte na **Další**.  
  
5.  Datový model připojení k databázi pomocí jedné z následujících kroků a potom klikněte na **Další**:  
  
    -   Pokud jste připojení k databázi již nakonfigurována, klikněte na tlačítko **nové připojení** a vytvořit nové připojení. Další informace najdete v tématu [postupy: vytvoření připojení databáze serveru SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631). To [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance musí mít ukázková databáze Northwind připojen.  
  
         \-nebo –  
  
    -   Pokud máte připojení k databázi již byla konfigurována pro připojení k databázi Northwind, vyberte ze seznamu připojení toto připojení.  
  
6.  Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políčka pro zobrazení a uložených procedur.  
  
7.  Klikněte na tlačítko **Dokončit** zavřete průvodce.  
  
    > [!NOTE]
    >  Tento model generované datové zpřístupní vlastnosti cizího klíče v typech entit. Datové modely, které jsou vytvořené pomocí sady Visual Studio 2008 nezahrnují tyto vlastnosti cizího klíče. Z toho důvodu je třeba aktualizovat třídy klienta služby data všech klientských aplikací, které byly vytvořeny pro přístup ke službě Northwind data, která byla vytvořena pomocí sady Visual Studio 2008 před pokusem o přístup k této verzi datové služby Northwind.  
  
### <a name="to-create-the-data-service"></a>Vytvoření datové služby  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název projektu ASP.NET a pak klikněte na tlačítko **přidat novou položku**.  
  
2.  V **přidat novou položku** dialogové okno, vyberte **služby ADO.NET Data**.  
  
3.  Název služby, zadejte `Northwind`.  
  
     Visual Studio vytvoří soubory značek a kódu XML pro novou službu. Ve výchozím nastavení otevře se okno editoru kódu. V **Průzkumníku**, služba bude mít název, Northwind, s příponou. svc.cs nebo. svc.vb.  
  
4.  V kódu pro službu data, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje službu data s typem, který je kontejneru entit datového modelu, který v tomto případě je `NorthwindEntities`. Definice třídy by měl vypadat to následující:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a>Viz také  
 [Vystavení dat jako službu](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
