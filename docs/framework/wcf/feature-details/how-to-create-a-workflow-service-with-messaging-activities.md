---
title: 'Postupy: Vytvoření služby pracovního postupu pomocí činnosti související se zprávami'
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: f5bb8df5936be1890bf744300daa7ccb68e341e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337770"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>Postupy: Vytvoření služby pracovního postupu pomocí činnosti související se zprávami
Toto téma popisuje, jak vytvořit jednoduchý pracovní postup službu pomocí aktivit zasílání zpráv. Toto téma se zaměřuje na mechanismu vytvoření služby pracovního postupu, kde se skládá pouze z aktivity zasílání zpráv služby. Ve službě reálného světa pracovní postup obsahuje mnoho dalších aktivit. Služba implementuje jednu operaci volat odezvu, která přebírá řetězec a vrátí řetězec volajícímu. Toto téma je první v řadě dvou tématech. Další téma [How To: Přístup k Service z aplikace pracovního postupu](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) popisuje, jak vytvořit aplikace pracovního postupu, která může volat služby vytvořené v tomto tématu.  
  
### <a name="to-create-a-workflow-service-project"></a>Chcete-li vytvořit projekt služby pracovního postupu  
  
1. Start Visual Studio 2012.  
  
2. Klikněte na tlačítko **souboru** nabídce vyberte možnost **nový**a potom **projektu** zobrazíte **dialogové okno nového projektu**. Vyberte **pracovního postupu** ze seznamu nainstalovaných šablon a **aplikace služeb pracovního postupu WCF** ze seznamu typů projektů. Pojmenujte projekt `MyWFService` a použijte výchozí umístění, jak je znázorněno na následujícím obrázku.  
  
     Klikněte na tlačítko **OK** tlačítka Zavřít **dialogové okno nového projektu**.  
  
3. Při vytvoření projektu souboru Service1.xamlx je otevřen v návrháři, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky ukazuje otevřít soubor Service1.xamlx v návrháři.](./media/how-to-create-a-workflow-service-with-messaging-activities/default-workflow-service.jpg)  
  
     Klikněte pravým tlačítkem na aktivitu s názvem **sekvenční služba** a vyberte **odstranit**.  
  
### <a name="to-implement-the-workflow-service"></a>K implementaci služby pracovního postupu  
  
1. Vyberte **nástrojů** karty na levé straně obrazovky zobrazte sadu nástrojů a klikněte na ikonu připínáčku nechat okno otevřené. Rozbalte **zasílání zpráv** oddílu na panelu zobrazíte zasílání zpráv aktivity a zasílání zpráv aktivity šablony, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky zobrazující nástrojů s oddílem zasílání zpráv rozšířit.](./media/how-to-create-a-workflow-service-with-messaging-activities/toolbox-messaging-section.jpg)  
  
2. Přetáhnout myší **ReceiveAndSendReply** šablona návrháře postupu provádění. Tím se vytvoří <xref:System.Activities.Statements.Sequence> aktivitu se **Receive** aktivity za nímž následuje <xref:System.ServiceModel.Activities.SendReply> aktivity, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky zobrazující šablony ReceiveAndSendReply](./media/how-to-create-a-workflow-service-with-messaging-activities/receiveandsendreply-template.jpg)  
  
     Všimněte si, že <xref:System.ServiceModel.Activities.SendReply> aktivity <xref:System.ServiceModel.Activities.SendReply.Request%2A> je nastavena na `Receive`, název <xref:System.ServiceModel.Activities.Receive> aktivitu, ke kterému <xref:System.ServiceModel.Activities.SendReply> odpovědi aktivity.  
  
3. V <xref:System.ServiceModel.Activities.Receive> typ aktivity `Echo` do textového pole s popiskem **OperationName**. Definuje název operace služba implementuje.  
  
     ![Snímek obrazovky, který ukazuje, kde zadejte název operace.](./media/how-to-create-a-workflow-service-with-messaging-activities/define-operation-name.jpg)  
  
4. S <xref:System.ServiceModel.Activities.Receive> aktivity vybrán, otevřete okno Vlastnosti není-li již otevřete kliknutím **zobrazení** nabídky a vyberete **okno vlastností**. V **okno vlastností** přejděte dolů, dokud se nezobrazí **CanCreateInstance** a klikněte na zaškrtávací políčko, jak je znázorněno na následujícím obrázku. Toto nastavení umožňuje vytvořit novou instanci služby (v případě potřeby), při doručení zprávy do hostitel služby pracovního postupu.  
  
     ![Snímek obrazovky s vlastností CanCreateInstance.](./media/how-to-create-a-workflow-service-with-messaging-activities/cancreateinstance-property.jpg)  
  
5. Vyberte <xref:System.Activities.Statements.Sequence> aktivity a kliknutím **proměnné** tlačítko v levém dolním rohu návrháře. Zobrazí se editor proměnné. Klikněte na tlačítko **vytvořit proměnnou** odkaz Přidat proměnnou pro uložení řetězce odeslané operace. Název proměnné `msg` a nastavte jeho **proměnnou** zadejte řetězec, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky, který ukazuje, jak přidat proměnnou.](./media/how-to-create-a-workflow-service-with-messaging-activities/add-variable-msg-string.jpg)  
  
     Klikněte na tlačítko **proměnné** tlačítko zavřete editor proměnné.  
  
6. Klikněte na tlačítko **definovat...** odkaz v **obsahu** textové pole <xref:System.ServiceModel.Activities.Receive> aktivita k zobrazení **definici obsahu** dialogového okna. Vyberte **parametry** přepínač, klikněte na tlačítko **přidat nový parametr** propojení, zadejte `inMsg` v **název** textového pole, vyberte **řetězec**v **typ** rozevírací seznam pole se seznamem a typ `msg` v **přiřadit k** textové pole, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky zobrazující, přidání parametrů obsahu.](./media/how-to-create-a-workflow-service-with-messaging-activities/adding-parameters-content.jpg)  
  
     Určuje, že aktivita Receive přijímá řetězcový parametr a že data svázaná s `msg` proměnné. Klikněte na tlačítko **OK** zavřete **definici obsahu** dialogového okna.  
  
7. Klikněte na tlačítko **definovat...**  odkaz v **obsahu** pole <xref:System.ServiceModel.Activities.SendReply> aktivita k zobrazení **definici obsahu** dialogového okna. Vyberte **parametry** přepínač, klikněte na tlačítko **přidat nový parametr** propojení, zadejte `outMsg` v **název** textové pole, vyberte **řetězec**v **typ** rozevíracího seznamu a `msg` v **hodnotu** textového pole, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky, který ukazuje, jak přidat parametr outMsg.](./media/how-to-create-a-workflow-service-with-messaging-activities/outmsg-parameters-content.jpg)  
  
     Určuje, který <xref:System.ServiceModel.Activities.SendReply> aktivita odesílá zprávy nebo typ kontraktu zprávy a že data svázaná s `msg` proměnné. Protože se jedná <xref:System.ServiceModel.Activities.SendReply> činnosti, to znamená, že data v `msg` slouží k naplnění zprávu aktivity odešle zpět klientovi. Klikněte na tlačítko **OK** zavřete **definici obsahu** dialogového okna.  
  
8. Uložit a sestavit řešení kliknutím **sestavení** nabídky a vyberete **sestavit řešení**.  
  
## <a name="configure-the-workflow-service-project"></a>Konfigurace projektu služby pracovního postupu  
 Služba pracovního postupu je dokončena. Tato část vysvětluje postup konfigurace řešení služby pracovního postupu k tomu, aby k hostování a spouštění. Toto řešení používá serveru ASP.NET Development Server k hostování služby.  
  
#### <a name="to-set-project-start-up-options"></a>Chcete-li nastavit možnosti spuštění projektu  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **MyWFService** a vyberte **vlastnosti** zobrazíte **vlastnosti projektu** dialogového okna.  
  
2. Vyberte **webové** kartě a vyberte **konkrétní stránka** pod **spustit akci** a typ `Service1.xamlx` do textového pole, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky ukazující dialogové okno Vlastnosti projektu.](./media/how-to-create-a-workflow-service-with-messaging-activities/project-properties-dialog.jpg)  
  
     To je hostitelem služby definované v Service1.xamlx na serveru ASP.NET Development Server.  
  
3. Stiskněte kombinaci kláves Ctrl + F5 ke spuštění služby. Ikona serveru ASP.NET Development Server se zobrazí v dolní pravé části plochy, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky zobrazující ikona technologie ASP.NET pro vývojáře serveru.](./media/how-to-create-a-workflow-service-with-messaging-activities/asp-net-dev-server-icon.jpg)  
  
     Kromě toho aplikace Internet Explorer zobrazí na stránce nápovědy služby WCF pro službu.  
  
     ![Snímek obrazovky zobrazující stránku nápovědy služby WCF.](./media/how-to-create-a-workflow-service-with-messaging-activities/wcf-service-help-page.jpg)  
  
4. Pokračovat k [jak: Přístup k Service z aplikace pracovního postupu](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) tématu k vytvoření klienta pracovní postup, který volá tuto službu.  
  
## <a name="see-also"></a>Viz také:

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Přehled hostování služeb pracovních postupů](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [Aktivity zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
