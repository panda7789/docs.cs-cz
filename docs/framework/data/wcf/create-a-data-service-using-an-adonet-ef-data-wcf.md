---
title: "Postupy: vytvoření služby Data pomocí zdroje dat ADO.NET Entity Framework (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9362aa6ea02f5878d2419ee7cbaab349cae27038
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Postupy: vytvoření služby Data pomocí zdroje dat ADO.NET Entity Framework (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zpřístupní entity data jako datové služby. Tato data entity zajišťuje [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Pokud zdroj dat je relační databáze. Toto téma ukazuje, jak vytvořit [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]– na základě datového modelu v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] webovou aplikaci, která je založena na existující databázi a použít tento datový model pro vytvoření nové datové služby.  
  
 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Také poskytuje nástroj pro příkazový řádek, který může vytvořit [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] modelu mimo [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] projektu. Další informace najdete v tématu [postupy: použití EdmGen.exe pro generování modelu a mapování soubory](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
### <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Chcete-li přidat model Entity Framework, který je založen na existující databázi a stávající webovou aplikaci  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
2.  V **šablony** podokně klikněte na tlačítko **Data** kategorie a potom vyberte **ADO.NET Entity Data Model**.  
  
3.  Zadejte název modelu a potom klikněte na **přidat**.  
  
     Na první stránku [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] průvodce se zobrazí.  
  
4.  V **zvolte obsah modelu** dialogové okno, vyberte **generování z databáze**. Pak klikněte na tlačítko **Další**.  
  
5.  Klikněte **nové připojení** tlačítko.  
  
6.  V **vlastnosti připojení** dialogové okno, zadejte název serveru, vyberte metodu ověřování, zadejte název databáze a pak klikněte na tlačítko **OK**.  
  
     **Vybrat datové připojení**dialogové okno s se aktualizuje se nastavení připojení k databázi.  
  
7.  Ujistěte se, že **uložit nastavení připojení entity v souboru App.Config jako:** je zaškrtnuté políčko. Pak klikněte na tlačítko **Další**.  
  
8.  V **zvolte si databázové objekty** dialogové okno, vyberte všechny databáze objekty, že chcete vystavit v rámci služby data.  
  
    > [!NOTE]
    >  Objektů obsažených v datovém modelu se službou data nezobrazí automaticky. Se musí být explicitně vystavené samotné služby. Další informace najdete v tématu [konfigurace službu Data](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
9. Klikněte na tlačítko **Dokončit** dokončete průvodce.  
  
     Tím se vytvoří výchozí datový model založena na konkrétní databázi. [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Umožňuje přizpůsobit datový model. Další informace najdete v tématu [úlohy](http://msdn.microsoft.com/en-us/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).  
  
### <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Chcete-li vytvořit službu data pomocí nového datového modelu  
  
1.  V [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], otevřete soubor EDMX, který představuje datový model.  
  
2.  V **prohlížeče modelu**, klikněte pravým tlačítkem na model, klikněte na **vlastnosti**a poznamenejte si název kontejneru entit.  
  
3.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název vaší [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu a pak klikněte na **přidat novou položku**.  
  
4.  V **přidat novou položku** dialogové okno, vyberte **služby WCF Data Service**.  
  
5.  Zadejte název pro službu a pak klikněte na tlačítko **OK**.  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]vytvoří soubory značek a kódu XML pro novou službu. Ve výchozím nastavení otevře se okno editoru kódu.  
  
6.  V kódu pro službu data, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje službu datového typu, který dědí z <xref:System.Data.Objects.ObjectContext> třídy a který je kontejneru entit datového modelu, který byl uvedeným v kroku 2.  
  
7.  V kódu pro službu data povolte autorizovaným klientům přístup k sad entit, že data služby vystavuje. Další informace najdete v tématu [vytváření službu Data](../../../../docs/framework/data/wcf/creating-the-data-service.md).  
  
8.  Chcete-li otestovat službu Northwind.svc data pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístupu ke službě z webového prohlížeče](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
## <a name="see-also"></a>Viz také  
 [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [Postupy: Vytvoření datové služby pomocí zdroje dat LINQ to SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
