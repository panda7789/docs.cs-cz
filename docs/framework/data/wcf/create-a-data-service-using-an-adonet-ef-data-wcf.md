---
title: 'Postupy: vytvoření datové služby pomocí zdroje dat Entity Framework ADO.NET (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 0aea4c21b5ea34cb0e8d944d37c879e918d6b27e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800573"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Postupy: vytvoření datové služby pomocí zdroje dat Entity Framework ADO.NET (WCF Data Services)

WCF Data Services zpřístupňuje data entit jako datovou službu. Tato data entity poskytuje rozhraní ADO. NETEntity, pokud je zdrojem dat relační databáze. V tomto tématu se dozvíte, jak vytvořit datový model založený Entity Framework ve webové aplikaci Visual Studio, která je založena na stávající databázi a pomocí tohoto datového modelu vytvořit novou datovou službu.

Entity Framework také poskytuje nástroj příkazového řádku, který může vygenerovat Entity Framework model mimo projekt sady Visual Studio. Další informace naleznete v tématu [How to: use EdmGen. exe ke generování modelu a mapování souborů](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Přidání modelu Entity Framework, který je založen na existující databázi, do existující webové aplikace

1. V nabídce **projekt** klikněte na příkaz **Přidat** > **novou položku**.

2. V podokně **šablony** klikněte na kategorii **dat** a pak vyberte **ADO.NET model EDM (Entity Data Model)** .

3. Zadejte název modelu a pak klikněte na **Přidat**.

     Zobrazí se první stránka průvodce model EDM (Entity Data Model).

4. V dialogovém okně **Vybrat obsah modelu** vyberte možnost **Generovat z databáze**. Pak klikněte na tlačítko **Další**.

5. Klikněte na tlačítko **nové připojení** .

6. V dialogovém okně **Vlastnosti připojení** zadejte název serveru, vyberte metodu ověřování, zadejte název databáze a klikněte na tlačítko **OK**.

     Dialogové okno **zvolit datové připojení** je aktualizováno nastavením připojení k databázi.

7. Ujistěte se, že je zaškrtnuté políčko **Uložit nastavení připojení entity v App. config jako:** . Pak klikněte na tlačítko **Další**.

8. V dialogovém okně **Zvolte objekty databáze** vyberte všechny databázové objekty, které chcete zpřístupnit v datové službě.

    > [!NOTE]
    > Objekty zahrnuté v datovém modelu nejsou automaticky zpřístupněny datovou službou. Musí být výslovně vystaveny samotným službám. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md).

9. Kliknutím na **Dokončit** průvodce dokončete.

     Tím se vytvoří výchozí datový model založený na konkrétní databázi. Entity Framework umožňuje přizpůsobit datový model. Další informace najdete v tématu [úlohy nástroje model EDM (Entity Data Model) Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Vytvoření datové služby pomocí nového datového modelu

1. V aplikaci Visual Studio otevřete soubor. edmx, který představuje datový model.

2. V **prohlížeči modelů**klikněte pravým tlačítkem na model, klikněte na **vlastnosti**a potom si poznamenejte název kontejneru entity.

3. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu ASP.NET a potom klikněte na **Přidat** > **Nová položka**.

4. V dialogovém okně **Přidat novou položku** vyberte šablonu **Služba WCF Data Service** ve **webové** kategorii.

   ![Šablona položky datové služby WCF v aplikaci Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Šablona **WCF Data Service** je k dispozici v aplikaci visual Studio 2015, ale ne v aplikaci visual Studio 2017 nebo novější.

5. Zadejte název služby a klikněte na tlačítko **OK**.

     Visual Studio vytvoří kód XML a soubory kódu pro novou službu. Ve výchozím nastavení se otevře okno Editor kódu.

6. V kódu pro datovou službu nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy definující datovou službu s typem, který dědí z třídy <xref:System.Data.Objects.ObjectContext> a který je kontejnerem entity datového modelu, který byl zaznamenán v kroku 2.

7. V kódu pro datovou službu povolte autorizovaným klientům přístup k sadám entit, které datová služba zpřístupňuje. Další informace najdete v tématu [Vytvoření datové služby](creating-the-data-service.md).

8. Chcete-li otestovat datovou službu Northwind. svc pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístup ke službě z webového prohlížeče](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Zprostředkovatelé datových služeb](data-services-providers-wcf-data-services.md)
- [Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe](create-a-data-service-using-rp-wcf-data-services.md)
- [Postupy: Vytvoření datové služby pomocí zdroje dat LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md)
