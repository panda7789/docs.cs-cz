---
title: Vytváření datové služby
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 781def411214b0804cdc094c00b2f655b6c3823d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="creating-the-data-service"></a>Vytváření datové služby
V této úloze se vytvoří služba ukázková data, která využívá [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vystavit [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu, který je založen na ukázková databáze Northwind. Úloha zahrnuje následující základní kroky:  
  
1.  Vytvoření [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové aplikace.  
  
2.  Definují model dat pomocí [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] nástroje.  
  
3.  Přidáte službu data do webové aplikace.  
  
4.  Povolte přístup ke službě data.  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Spuštění webové aplikace, který vytvoříte po dokončení této úlohy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojový Server poskytované sadě Visual Studio. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Vývojový Server podporuje pouze přístup z místního počítače. Chcete-li také usnadňují testování a řešení potíží s službu data během vývoje, zvažte spuštění aplikace, který je hostitelem služby data pomocí Internetové informační služby (IIS). Další informace najdete v tématu [postup: vývoj WCF Data Service spuštěna ve službě IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
### <a name="to-create-the-aspnet-web-application"></a>K vytvoření aplikace technologie ASP.NET  
  
1.  V sadě Visual Studio na **soubor** nabídce vyberte možnost **nový**a potom vyberte **projektu**.  
  
2.  V **nový projekt** dialogové okno, v části jazyka Visual Basic a Visual C# vyberte **webové** šablony a potom vyberte **webové aplikace ASP.NET**.  
  
    > [!NOTE]
    >  Pokud používáte Visual Studio Web Developer, musíte vytvořit nový web místo novou webovou aplikaci.  
  
3.  Typ `NorthwindService` jako název projektu.  
  
4.  Click **OK**.  
  
5.  (Volitelné) Zadejte číslo portu specifické pro vaši webovou aplikaci. Poznámka: číslo portu `12345` se používá ve zbývající části rychlý start.  
  
    1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, že jste právě vytvořili a potom klikněte na **vlastnosti**.  
  
    2.  Vyberte **webové** kartě a nastavte hodnotu **specifického portu** textové pole k `12345`.  
  
### <a name="to-define-the-data-model"></a>Chcete-li definovat datový model  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu a pak klikněte na tlačítko **přidat novou položku.**  
  
2.  V **přidat novou položku** dialogové okno, klikněte **Data** šablony a potom vyberte **ADO.NET Entity Data Model**.  
  
3.  Zadejte název datového modelu, `Northwind.edmx`.  
  
4.  V [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] průvodce vyberte **generování z databáze**a potom klikněte na **Další**.  
  
5.  Datový model připojení k databázi pomocí jedné z následujících kroků a potom klikněte na **Další**:  
  
    -   Pokud jste připojení k databázi již nakonfigurována, klikněte na tlačítko **nové připojení** a vytvořit nové připojení. Další informace najdete v tématu [postupy: vytvoření připojení databáze serveru SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631). Tato instance systému SQL Server musí mít ukázková databáze Northwind připojen.  
  
         \- nebo –  
  
    -   Pokud máte připojení k databázi již byla konfigurována pro připojení k databázi Northwind, vyberte ze seznamu připojení toto připojení.  
  
6.  Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políčka pro zobrazení a uložených procedur.  
  
7.  Klikněte na tlačítko **Dokončit** zavřete průvodce.  
  
    > [!NOTE]
    >  Tento model generované datové zpřístupní vlastnosti cizího klíče v typech entit. Datové modely, které jsou vytvořené pomocí sady Visual Studio 2008 nezahrnují tyto vlastnosti cizího klíče. Z toho důvodu je třeba aktualizovat třídy klienta služby data všech klientských aplikací, které byly vytvořeny pro přístup ke službě Northwind data, která byla vytvořena pomocí sady Visual Studio 2008 před pokusem o přístup k této verzi datové služby Northwind.  
  
### <a name="to-create-the-data-service"></a>Vytvoření datové služby  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název vaší [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu a pak klikněte na **přidat novou položku**.  
  
2.  V **přidat novou položku** dialogové okno, vyberte **služby WCF Data Service**.  
  
3.  Název služby, zadejte `Northwind`.  
  
     Visual StudioVisual Studio vytvoří soubory značek a kódu XML pro novou službu. Ve výchozím nastavení otevře se okno editoru kódu. V **Průzkumníku**, služba bude mít název, Northwind, s příponou. svc.cs nebo. svc.vb.  
  
4.  V kódu pro službu data, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje službu data s typem, který je kontejneru entit datového modelu, který v tomto případě je `NorthwindEntities`. Definice třídy by měl vypadat to následující:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a>Chcete-li povolit přístup k datovým prostředkům služby  
  
1.  V kódu pro službu data, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     To umožňuje autorizovaným klientům ke čtení a zápisu přístup k prostředkům pro zadanou entitu sady.  
  
    > [!NOTE]
    >  Libovolného klienta, kterému mají přístup [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace může také přístup k prostředkům vystavené službu data. V produkčním datové služby aby se zabránilo neoprávněnému přístupu k prostředkům byste měli také zabezpečit vlastní aplikace. Další informace najdete v tématu [zabezpečení služby WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="next-steps"></a>Další kroky  
 Úspěšně jste vytvořili novou službu data, která zveřejňuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu, který je založen na ukázková databáze Northwind a jste povolili přístup k informačnímu kanálu pro klienty, kteří mají oprávnění na [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové aplikace. V dalším kroku se spustí službu data ze sady Visual Studio a budou přistupovat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu odesláním požadavky HTTP GET prostřednictvím webového prohlížeče:  
  
 [Přístup ke službě z webového prohlížeče](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>Viz také  
 [Nástroje modelu ADO.NET Entity Data Model](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
