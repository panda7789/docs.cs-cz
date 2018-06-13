---
title: 'Postupy: Přístup ke službě z aplikace pracovního postupu'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 5f1ef07d92eea2b526259cd11caf56e45c83675d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494935"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Postupy: Přístup ke službě z aplikace pracovního postupu
Toto téma popisuje způsob volání služby pracovního postupu z konzolové aplikace pracovního postupu. Závisí na dokončení [postupy: vytvoření služby pracovního postupu s aktivitami zasílání zpráv](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tématu. I když toto téma popisuje způsob volání služby pracovního postupu z aplikace pracovního postupu, stejné metody slouží k volání žádné služby Windows Communication Foundation (WCF) z aplikace pracovního postupu.  
  
### <a name="create-a-workflow-console-application-project"></a>Vytvoření projektu konzolové aplikace pracovního postupu  
  
1.  Spustit [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Načtení projektu MyWFService jste vytvořili v [postupy: vytvoření služby pracovního postupu s aktivitami zasílání zpráv](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tématu.  
  
3.  Klikněte pravým tlačítkem **MyWFService** řešení **Průzkumníku řešení** a vyberte **přidat**, **nový projekt**. Vyberte **pracovního postupu** v **nainstalovaných šablonách** a **pracovního postupu konzolové aplikace** ze seznamu typy projektů. Název projektu MyWFClient a použít výchozí umístění, jak je znázorněno na následujícím obrázku.  
  
     ![Přidat dialogové okno Nový projekt](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")  
  
     Klikněte na tlačítko **OK** tlačítko pro zavření **přidat dialogové okno Nový projekt**.  
  
4.  Po vytvoření projektu je Workflow1.xaml soubor otevřít v návrháři. Klikněte **sada nástrojů** otevřete sady nástrojů, pokud není již otevřete a klikněte na ikonu připínáčku nechat otevřené okno panel nástrojů.  
  
5.  Stisknutím kombinace kláves Ctrl + F5 pro sestavení a spuštění služby. Jako dříve se spustí vývojový Server ASP.NET a Internet Explorer zobrazí na stránce nápovědy WCF. Všimněte si identifikátor URI pro tuto stránku, jako je nutné použít v dalším kroku.  
  
     ![IE zobrazení stránce nápovědy k WCF a identifikátoru URI](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")  
  
6.  Klikněte pravým tlačítkem **MyWFClient** v projektu **Průzkumníku řešení** a vyberte **přidat odkaz na službu**. Klikněte na tlačítko **Discover** tlačítko Hledat aktuální řešení pro všechny služby. Klepněte na trojúhelník vedle Service1.xamlx v seznamu služeb. Klepněte na trojúhelník vedle Service1 seznam kontrakty implementované Service1 služby. Rozbalte **Service1** uzlu **služby** seznamu. Operaci Echo se zobrazí v **Operations** seznamu, jak je znázorněno na následujícím obrázku.  
  
     ![Přidat odkaz na službu – dialogové okno](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "AddServiceReference")  
  
     Ponechat výchozí obor názvů a klikněte na tlačítko **OK** pro zavření **přidat odkaz na službu** dialogové okno. Zobrazí se následující dialogové okno.  
  
     ![Dialogové okno Přidat služby odkaz oznámení](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")  
  
     Klikněte na tlačítko **OK** zavřete dialogové okno. Stiskněte klávesu CTRL + SHIFT + B řešení sestavíte. Volá se upozornění v panelu nástrojů, byla přidána nová část **MyWFClient.ServiceReference1.Activities**. Rozbalením tohoto oddílu a Všimněte si Echo aktivity, která byla přidána jak je znázorněno na následujícím obrázku.  
  
     ![Echo aktivity v sadě nástrojů](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")  
  
7.  Přetáhnout myší <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` aktivity na plochu návrháře. Je pod **tok řízení** oddílu na panelu.  
  
8.  S <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` aktivity v fokus, klikněte **proměnné** propojení a přidejte řetězcové proměnné s názvem `inString`. Zadejte výchozí hodnotu proměnné `"Hello, world"` a také řetězec proměnné s názvem `outString` jak je znázorněno v následujícím diagramu.  
  
     ![Přidání proměnné](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")  
  
9. Přetáhnout myší **Echo** aktivity do <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`. V okně vlastností vytvořit vazbu `inMsg` argument `inString` proměnné a `outMsg` argument `outString` proměnné, jak je znázorněno na následujícím obrázku. To předá hodnotu `inString` proměnnou operaci a potom provede návratovou hodnotu a umístí jej do `outString` proměnné.  
  
     ![Vytvoření vazby argumentů proměnných](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")  
  
10. Přetáhnout myší **WriteLine** aktivity níže **Echo** aktivita se má zobrazit řetězec vrácený volání služby. **WriteLine** aktivity se nachází v **primitiv** uzlu v panelu nástrojů. Vytvoření vazby **Text** argument **WriteLine** aktivitu `outString` proměnné tak, že zadáte `outString` do textového pole na **WriteLine** aktivity. Pracovní postup by teď měl vypadat jako na následujícím obrázku.  
  
     ![Pracovní postup dokončení klienta](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")  
  
11. Klikněte pravým tlačítkem na řešení MyWFService a vyberte **nastavit projekty po spuštění...** . Vyberte **více projektů po spuštění** přepínač a vyberte **spustit** pro každý projekt v **akce** sloupce, jak je znázorněno na následujícím obrázku.  
  
     ![Spuštění projekty možnosti](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "StartupProjects")  
  
12. Stiskněte kombinaci kláves Ctrl + F5 spusťte službu a klienta. Vývojový Server ASP.NET hostuje službu, Internet Explorer zobrazí na stránce nápovědy WCF a klientská aplikace pracovního postupu se spustí v okně konzoly a zobrazí řetězec vrácená ze služby ("Hello, world").  
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Postupy: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [Využívání z pracovního postupu v projektu webové služby WCF](http://go.microsoft.com/fwlink/?LinkId=207725)
