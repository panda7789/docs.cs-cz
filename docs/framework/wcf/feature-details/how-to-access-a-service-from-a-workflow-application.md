---
title: 'Postupy: Přístup ke službě z aplikace pracovního postupu'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 2ce79b726b623c2a25bf14065682e685455ca575
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597238"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Postupy: Přístup ke službě z aplikace pracovního postupu
Toto téma popisuje, jak volat službu pracovního postupu z konzolové aplikace pracovního postupu. Závisí na dokončení postupu [: vytvoření služby pracovního postupu pomocí aktivity zasílání zpráv](how-to-create-a-workflow-service-with-messaging-activities.md) . I když toto téma popisuje, jak volat službu pracovního postupu z aplikace pracovního postupu, stejné metody lze použít k volání libovolné služby Windows Communication Foundation (WCF) z aplikace pracovního postupu.

### <a name="create-a-workflow-console-application-project"></a>Vytvoření projektu konzolové aplikace pracovního postupu

1. Spusťte Visual Studio 2012.

2. Načtěte projekt MyWFService, který jste vytvořili v tématu [Postupy: vytvoření služby pracovního postupu pomocí aktivity zasílání zpráv](how-to-create-a-workflow-service-with-messaging-activities.md) .

3. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení **MyWFService** a vyberte **Přidat**, **Nový projekt**. V seznamu typů projektů vyberte **pracovní postup** v části **Nainstalované šablony** a **Konzolová aplikace pracovního postupu** . Pojmenujte projekt MyWFClient a použijte výchozí umístění, jak je znázorněno na následujícím obrázku.

     ![Dialogové okno Přidat nový projekt](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     Kliknutím na tlačítko **OK** zavřete **dialogové okno Přidat nový projekt**.

4. Po vytvoření projektu se soubor Workflow1. XAML otevře v návrháři. Kliknutím na kartu **panelu nástrojů** otevřete panel nástrojů, pokud ještě není otevřený, a kliknutím na připínáček zachováte okno sady nástrojů otevřené.

5. Stisknutím klávesy **CTRL** + **F5** Sestavte a spusťte službu. Stejně jako dřív se spustí vývojový server ASP.NET a Internet Explorer zobrazí stránku s usnadněním pro WCF. Všimněte si identifikátoru URI této stránky, protože je nutné ji použít v dalším kroku.

     ![IE zobrazení stránky a identifikátoru URI v nápovědě WCF](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt **MyWFClient** a vyberte **Přidat**  >  **odkaz na službu**. Kliknutím na tlačítko **Vyhledat** můžete vyhledat aktuální řešení pro všechny služby. V seznamu služeb klikněte na trojúhelník vedle Service1. xamlx. Kliknutím na trojúhelník vedle Service1 zobrazíte seznam kontraktů implementovaných službou Service1. Rozbalte uzel **Service1** v seznamu **služby** . Operace ECHO se zobrazí v seznamu **operací** , jak je znázorněno na následujícím obrázku.

     ![Dialog Přidat odkaz na službu](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     Ponechte výchozí obor názvů a kliknutím na tlačítko **OK** zavřete dialogové okno **Přidat odkaz na službu** . Zobrazí se následující dialogové okno.

     ![Dialog oznámení Přidat odkaz na službu](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     Kliknutím na tlačítko **OK** zavřete dialogové okno. Potom stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení. Všimněte si, že v sadě nástrojů byla přidána nová část s názvem **MyWFClient. ServiceReference1. Activities**. Rozbalte tuto část a Všimněte si aktivity ozvěny, která byla přidána, jak je znázorněno na následujícím obrázku.

     ![Aktivita echo v sadě nástrojů](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7. Přetáhněte <xref:System.Activities.Statements.Sequence> aktivitu na plochu návrháře. Je pod částí **tok řízení** v sadě nástrojů.

8. U <xref:System.Activities.Statements.Sequence> aktivity, která je zaostření, klikněte na odkaz **proměnné** a přidejte řetězcovou proměnnou s názvem `inString` . Poskytněte proměnné výchozí hodnotu `"Hello, world"` a také řetězcovou proměnnou s názvem `outString` , jak je znázorněno v následujícím diagramu.

     ![Přidání proměnné inString](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. Přetáhněte aktivitu **echo** do umístění <xref:System.Activities.Statements.Sequence> . V okně Vlastnosti svažte `inMsg` argument `inString` proměnné a `outMsg` argument `outString` proměnné, jak je znázorněno na následujícím obrázku. Tato operace projde hodnotou `inString` proměnné pro operaci a poté převezme návratovou hodnotu a umístí ji do `outString` proměnné.

     ![Vazba argumentů na proměnné](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. Přetáhněte aktivitu **WriteLine** pod aktivitu **echo** a zobrazte tak řetězec vrácený voláním služby. Aktivita **WriteLine** se nachází v uzlu **primitivních elementů** v sadě nástrojů. Navažte **textový** argument aktivity **WriteLine** na `outString` proměnnou tak, že zadáte `outString` do textového pole v aktivitě **WriteLine** . Pracovní postup by teď měl vypadat jako na následujícím obrázku.

     ![Kompletní pracovní postup klienta](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. Klikněte pravým tlačítkem na řešení MyWFService a vyberte **nastavit projekty po spuštění...**. Vyberte přepínač **více projektů po spuštění** a vyberte **Spustit** pro každý projekt ve sloupci **Akce** , jak je znázorněno na následujícím obrázku.

     ![Možnosti projektů po spuštění](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. Stisknutím kombinace kláves CTRL + F5 spusťte službu i klienta. ASP.NET Development Server hostuje službu, Internet Explorer zobrazí stránku s technickou pomocí WCF a aplikace pracovního postupu klienta se spustí v okně konzoly a zobrazí řetězec vrácený službou ("Hello, World").

## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](workflow-services.md)
- [Postupy: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv](how-to-create-a-workflow-service-with-messaging-activities.md)
- [Využívání služby WCF z pracovního postupu ve webovém projektu](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
