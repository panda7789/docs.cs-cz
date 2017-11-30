---
title: "Postup: Vytvoření služby pracovního postupu pomocí činnosti související se zprávami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b2f418298b5b937b5d4c7af2bd2def38c5827e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>Postup: Vytvoření služby pracovního postupu pomocí činnosti související se zprávami
Toto téma popisuje postup vytvoření jednoduchého pracovního postupu služby pomocí aktivity zasílání zpráv. Toto téma se zaměřuje na mechanismů vytvoření služby pracovního postupu, kde se služba se skládá pouze z aktivity zasílání zpráv. Ve službě reálného pracovní postup obsahuje mnoho dalších aktivit. Služba se implementuje jedna operace s názvem odezvu, která přebírá řetězec a vrátí řetězec volajícímu. Toto téma je první v řadě dvou tématech. Dalším tématu [postupy: přístup z pracovní postup aplikace služby](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) popisuje, jak vytvořit aplikaci pracovního postupu, která můžete volat službě vytvořené v tomto tématu.  
  
### <a name="to-create-a-workflow-service-project"></a>Vytvoření projektu služby pracovního postupu  
  
1.  Spustit [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Klikněte na tlačítko **soubor** nabídce vyberte možnost **nový**a potom **projektu** zobrazíte **dialogové okno Nový projekt**. Vyberte **pracovního postupu** ze seznamu nainstalovaných šablon a **aplikace služby pracovního postupu WCF** ze seznamu typy projektů. Název projektu `MyWFService` a použít výchozí umístění, jak je znázorněno na následujícím obrázku.  
  
     Klikněte na tlačítko **OK** tlačítko pro zavření **dialogové okno Nový projekt**.  
  
3.  Při vytváření projektu je Service1.xamlx soubor otevřít v návrháři, jak je znázorněno na následujícím obrázku.  
  
     ![Výchozí pracovní postup zobrazí v návrháři](../../../../docs/framework/wcf/feature-details/media/defaultworkflowservice.JPG "DefaultWorkflowService")  
  
     Klikněte pravým tlačítkem na aktivitu s názvem bez přípony **sekvenční služby** a vyberte **odstranit**.  
  
### <a name="to-implement-the-workflow-service"></a>K implementaci služby pracovního postupu  
  
1.  Vyberte **sada nástrojů** karty na levé straně obrazovky a zobrazení panelu klikněte na ikonu připínáčku nechat otevřené okno. Rozbalte **zasílání zpráv** oddílu na panelu zobrazíte aktivity zasílání zpráv a zasílání zpráv šablony aktivit, jak je znázorněno na následujícím obrázku.  
  
     ![Rozšířit nástrojů zasílání zpráv karta](../../../../docs/framework/wcf/feature-details/media/wfdesignertoolbox.JPG "WFDesignerToolbox")  
  
2.  Přetáhnout myší **ReceiveAndSendReply** šablona návrháře pracovních postupů. Tím se vytvoří <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` aktivitu **Receive** následuje aktivity <xref:System.ServiceModel.Activities.SendReply> aktivity, jak je znázorněno na následujícím obrázku.  
  
     ![ReceiveAndSendReply šablona v návrháři](../../../../docs/framework/wcf/feature-details/media/receiveandsendreply.JPG "ReceiveAndSendReply")  
  
     Všimněte si, že <xref:System.ServiceModel.Activities.SendReply> aktivity <xref:System.ServiceModel.Activities.SendReply.Request%2A> je nastavena na `Receive`, název <xref:System.ServiceModel.Activities.Receive> aktivity, ke kterému <xref:System.ServiceModel.Activities.SendReply> aktivity je odeslání odpovědi.  
  
3.  V <xref:System.ServiceModel.Activities.Receive> typ aktivity `Echo` do textového pole s názvem bez přípony **OperationName**. Definuje název operace služby implementuje.  
  
     ![Zadejte název operace](../../../../docs/framework/wcf/feature-details/media/defineoperation.JPG "DefineOperation")  
  
4.  S <xref:System.ServiceModel.Activities.Receive> aktivity vybrána, otevřete okno Vlastnosti není-li již otevřete kliknutím **zobrazení** nabídky a výběrem **vlastnosti – okno**. V **vlastnosti – okno** přejděte dolů do části **CanCreateInstance** a klikněte na zaškrtávací políčko, jak je znázorněno na následujícím obrázku. Toto nastavení umožňuje hostitele služby pracovního postupu pro vytvoření nové instance služby (v případě potřeby) při příjmu zprávy.  
  
     ![Vlastnost CanCreateInstance](../../../../docs/framework/wcf/feature-details/media/cancreateinstance.JPG "CanCreateInstance")  
  
5.  Vyberte <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` aktivity a klikněte na tlačítko **proměnné** tlačítko v levém dolním rohu návrháře. Zobrazí se editor proměnných. Klikněte na tlačítko **vytvořit proměnnou** odkaz Přidat proměnnou pro uložení řetězec posílá operaci. Název proměnné `msg` a nastavit jeho **proměnná** zadejte řetězec, jak je znázorněno na následujícím obrázku.  
  
     ![Přidejte proměnnou](../../../../docs/framework/wcf/feature-details/media/addvariable.JPG "AddVariable")  
  
     Klikněte **proměnné** tlačítko zavřete editor proměnných.  
  
6.  Klikněte **definovat...** odkaz **obsahu** textového pole <xref:System.ServiceModel.Activities.Receive> aktivita se má zobrazit **obsahu definice** dialogové okno. Vyberte **parametry** přepínač, klikněte na tlačítko **přidat nový parametr** , zadejte `inMsg` v **název** textového pole, vyberte **řetězec**v **typ** rozevírací pole se seznamem a typ `msg` v **přiřadit k** textového pole, jak je znázorněno na následujícím obrázku.  
  
     ![Přidávání obsahu parametry](../../../../docs/framework/wcf/feature-details/media/parameterscontent.jpg "ParametersContent")  
  
     Určuje, že aktivitu příjmu přijímá řetězcový parametr a že dat je vázána na `msg` proměnné. Klikněte na tlačítko **OK** zavřete **obsahu definice** dialogové okno.  
  
7.  Klikněte **definovat...**  odkaz **obsahu** pole <xref:System.ServiceModel.Activities.SendReply> aktivita se má zobrazit **obsahu definice** dialogové okno. Vyberte **parametry** přepínač, klikněte na tlačítko **přidat nový parametr** , zadejte `outMsg` v **název** textovému poli, vyberte **řetězec**v **typ** rozevíracím seznamu, a `msg` v **hodnotu** textového pole, jak je znázorněno na následujícím obrázku.  
  
     ![Přidávání obsahu parametry](../../../../docs/framework/wcf/feature-details/media/parameterscontent2.jpg "ParametersContent2")  
  
     To určuje, že <xref:System.ServiceModel.Activities.SendReply> aktivity odešle zpráva nebo zpráva typu kontraktu a dat je vázána `msg` proměnné. Protože se jedná <xref:System.ServiceModel.Activities.SendReply> aktivity, to znamená, data v `msg` se používá k naplnění zpráva aktivita odesílá zpět do klienta. Klikněte na tlačítko **OK** zavřete **obsahu definice** dialogové okno.  
  
8.  Uložit a sestavit řešení kliknutím **sestavení** nabídky a výběrem **sestavit řešení**.  
  
## <a name="configure-the-workflow-service-project"></a>Konfigurace projektu služby pracovního postupu  
 Služby pracovních postupů je dokončena. Tato část vysvětluje postup konfigurace usnadňují hostování a spuštění řešení služby pracovního postupu. Toto řešení používá k hostování služby vývojový Server ASP.NET.  
  
#### <a name="to-set-project-start-up-options"></a>Chcete-li nastavit možnosti spuštění projektu  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **MyWFService** a vyberte **vlastnosti** zobrazíte **vlastnosti projektu** dialogové okno.  
  
2.  Vyberte **webové** a vyberte **konkrétní stránky** pod **spustit akci** a typ `Service1.xamlx` do textového pole, jak je znázorněno na následujícím obrázku.  
  
     ![Dialogové okno Vlastnosti projekt](../../../../docs/framework/wcf/feature-details/media/projectpropertiesdlg.JPG "ProjectPropertiesDlg")  
  
     To je hostitelem služby definované v Service1.xamlx v vývojový Server ASP.NET.  
  
3.  Stiskněte kombinaci kláves Ctrl + F5 spusťte službu. Jak je znázorněno na následujícím obrázku, zobrazí se ikona vývojový Server ASP.NET na pravé straně nižší plochy.  
  
     ![Ikona serveru ASP.NET vývojáře](../../../../docs/framework/wcf/feature-details/media/aspnetdevservericon.JPG "ASPNETDEVServerIcon")  
  
     Kromě toho Internet Explorer zobrazí na stránce nápovědy služby WCF pro službu.  
  
     ![Stránka nápovědy WCF](../../../../docs/framework/wcf/feature-details/media/wcfhelppate.JPG "WCFHelpPate")  
  
4.  Pokračujte na [postupy: přístup z pracovní postup aplikace služby](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) tématu, které chcete vytvořit pracovní postup klienta, který volá tuto službu.  
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Přehled hostování služeb pracovních postupů](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [Aktivity zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
