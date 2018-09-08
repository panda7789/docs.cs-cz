---
title: 'Postupy: vytvoření datové služby pomocí zdroji dat ADO.NET Entity Framework (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 72439596ec6dc6c42024ed38116ba0026922154c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180706"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Postupy: vytvoření datové služby pomocí zdroji dat ADO.NET Entity Framework (WCF Data Services)

Služby WCF Data Services zpřístupňuje entity data jako datové služby. Tato entita poskytuje společnost [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Pokud zdroj dat je relační databáze. V tomto tématu se dozvíte, jak vytvořit [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]– na základě datového modelu v aplikaci Visual Studio Web, který je založený na existující databáze a tento model dat slouží k vytvoření nové datové služby.

[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Poskytuje nástroj příkazového řádku, který můžete vygenerovat také [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model mimo projekt sady Visual Studio. Další informace najdete v tématu [postupy: použití EdmGen.exe pro generování modelu a souborů mapování](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Chcete-li přidat model Entity Framework, která je založena na existující databázi do existující webové aplikace

1. Na **projektu** nabídky, klikněte na tlačítko **přidat** > **nová položka**.

2. V **šablony** podokně klikněte na tlačítko **Data** kategorie a pak vyberte **datový Model Entity ADO.NET**.

3. Zadejte název modelu a poté klikněte na tlačítko **přidat**.

     První stránka [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] průvodce se zobrazí.

4. V **výběr obsahu modelu** dialogu **Generovat z databáze**. Pak klikněte na tlačítko **Další**.

5. Klikněte na tlačítko **nové připojení** tlačítko.

6. V **vlastnosti připojení** dialogové okno, zadejte název vašeho serveru, vyberte metodu ověřování, zadejte název databáze a pak klikněte na tlačítko **OK**.

     **Vyberte datové připojení**dialogové okno s se aktualizuje se nastavení připojení k databázi.

7. Ujistěte se, že **uložit nastavení připojení v souboru App.Config jako entity:** je zaškrtnuté políčko. Pak klikněte na tlačítko **Další**.

8. V **zvolte vaše databázové objekty** dialogové okno, vyberte všechny databáze objekty chcete vystavit v datové služby.

    > [!NOTE]
    > Objektů obsažených v datovém modelu nejsou datovou službou vystavena automaticky. Musí být explicitně vystavené samotné služby. Další informace najdete v tématu [konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

9. Klikněte na tlačítko **Dokončit** kroky průvodce dokončete.

     Tím se vytvoří výchozí datový model založený na konkrétní databáze. [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Umožňuje Přizpůsobte si datový model. Další informace najdete v tématu [úlohy](https://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Vytvoření datové služby s použitím nového datového modelu

1. V sadě Visual Studio otevřete soubor EDMX, který představuje datový model.

2. V **prohlížeč modelu**, klikněte pravým tlačítkem na model, klikněte na tlačítko **vlastnosti**a potom si poznamenejte název kontejneru entity.

3. V **Průzkumníka řešení**, klikněte pravým tlačítkem na název vaší [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu a pak klikněte na tlačítko **přidat** > **nová položka**.

4. V **přidat novou položku** dialogové okno, vyberte **službu WCF Data Service** šablony **webové** kategorie.

   ![Služby WCF Data Service šablony položky v sadě Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **Službu WCF Data Service** šablona je k dispozici v sadě Visual Studio 2015, ale ne v sadě Visual Studio 2017.

5. Zadejte název pro službu a pak klikněte na tlačítko **OK**.

     Visual Studio vytvoří soubory značek a kódu XML pro novou službu. Ve výchozím nastavení otevře se okno editoru kódu.

6. V kódu pro datovou službu, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje datové služby s typem, který dědí z <xref:System.Data.Objects.ObjectContext> třídy, který je kontejner entit datového modelu, který byl jste si poznamenali v kroku 2.

7. V kódu pro datovou službu povolte autorizovaným klientům přístup k sady entit, které služba data zpřístupňuje. Další informace najdete v tématu [vytvoření datové služby](../../../../docs/framework/data/wcf/creating-the-data-service.md).

8. Pokud chcete testovat službu Northwind.svc dat pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístupu ke službě z webového prohlížeče](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Viz také

- [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [Postupy: Vytvoření datové služby pomocí zdroje dat LINQ to SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)