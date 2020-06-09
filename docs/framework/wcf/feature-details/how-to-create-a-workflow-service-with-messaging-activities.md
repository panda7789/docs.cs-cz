---
title: 'Postup: Vytvoření služby pracovního postupu pomocí činnosti související se zprávami'
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: b4991fc9f8a6c45cae3943f1506247c42ed2b30b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597121"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>Postup: Vytvoření služby pracovního postupu pomocí činnosti související se zprávami
Toto téma popisuje, jak vytvořit jednoduchou službu pracovního postupu pomocí aktivit zasílání zpráv. Toto téma se zaměřuje na mechanismy vytvoření služby pracovního postupu, kde se služba skládá výhradně z aktivit zasílání zpráv. Pracovní postup v reálné službě obsahuje mnoho dalších aktivit. Služba implementuje jednu operaci s názvem echo, která převezme řetězec a vrátí řetězec volajícímu. Toto téma je první v řadě dvou témat. Další téma [Postupy: přístup ke službě z aplikace pracovního postupu](how-to-access-a-service-from-a-workflow-application.md) popisuje, jak vytvořit aplikaci pracovního postupu, která může volat službu vytvořenou v tomto tématu.  
  
### <a name="to-create-a-workflow-service-project"></a>Vytvoření projektu služby pracovního postupu  
  
1. Spusťte Visual Studio 2012.  
  
2. Klikněte na nabídku **soubor** , vyberte **Nový**a pak na **projekt** k zobrazení **dialogového okna Nový projekt**. V seznamu typů projektů vyberte **pracovní postup** ze seznamu nainstalovaných šablon a **aplikace služby pracovního postupu WCF** . Pojmenujte projekt `MyWFService` a použijte výchozí umístění, jak je znázorněno na následujícím obrázku.  
  
     Kliknutím na tlačítko **OK** zavřete **dialogové okno Nový projekt**.  
  
3. Po vytvoření projektu se v Návrháři otevře soubor Service1. xamlx, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky se v Návrháři zobrazuje v otevřeném souboru Service1. xamlx.](./media/how-to-create-a-workflow-service-with-messaging-activities/default-workflow-service.jpg)  
  
     Klikněte pravým tlačítkem na aktivitu s označením **sekvenční služba** a vyberte **Odstranit**.  
  
### <a name="to-implement-the-workflow-service"></a>Implementace služby pracovního postupu  
  
1. Vyberte kartu **panel nástrojů** na levé straně obrazovky a zobrazte tak sadu nástrojů a kliknutím na připínáček nechejte okno otevřené. Rozbalením části **zasílání zpráv** v sadě nástrojů zobrazíte aktivity zasílání zpráv a šablony aktivity zasílání zpráv, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky, který zobrazuje rozbalenou část sada nástrojů se správou zpráv.](./media/how-to-create-a-workflow-service-with-messaging-activities/toolbox-messaging-section.jpg)  
  
2. Přetáhněte šablonu **ReceiveAndSendReply** do návrháře pracovních postupů. Tím se vytvoří <xref:System.Activities.Statements.Sequence> aktivita s aktivitou **Receive** následovanou <xref:System.ServiceModel.Activities.SendReply> aktivitou, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky zobrazující šablonu ReceiveAndSendReply](./media/how-to-create-a-workflow-service-with-messaging-activities/receiveandsendreply-template.jpg)  
  
     Všimněte si, že <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.SendReply.Request%2A> vlastnost aktivity je nastavena na `Receive` , název aktivity, <xref:System.ServiceModel.Activities.Receive> na kterou <xref:System.ServiceModel.Activities.SendReply> je aktivita odpovědná.  
  
3. V <xref:System.ServiceModel.Activities.Receive> typu aktivity `Echo` do textového pole s popiskem název **operace**. Tím se definuje název operace, kterou služba implementuje.  
  
     ![Snímek obrazovky, který ukazuje, kde zadat název operace.](./media/how-to-create-a-workflow-service-with-messaging-activities/define-operation-name.jpg)  
  
4. Když je <xref:System.ServiceModel.Activities.Receive> Vybraná aktivita, otevřete okno Vlastnosti, pokud ještě není otevřené, a to kliknutím na nabídku **zobrazení** a výběrem **okna vlastnosti**. V **okně Vlastnosti** se posuňte dolů, dokud se nezobrazí **CanCreateInstance** a klikněte na zaškrtávací políčko, jak je znázorněno na následujícím obrázku. Toto nastavení umožňuje, aby hostitel služby pracovního postupu při přijetí zprávy vytvořil novou instanci služby (v případě potřeby).  
  
     ![Snímek obrazovky zobrazující vlastnost CanCreateInstance](./media/how-to-create-a-workflow-service-with-messaging-activities/cancreateinstance-property.jpg)  
  
5. Vyberte <xref:System.Activities.Statements.Sequence> aktivitu a klikněte na tlačítko **proměnné** v levém dolním rohu návrháře. Tím se zobrazí Editor proměnných. Kliknutím na odkaz **vytvořit proměnnou** přidáte proměnnou pro uložení řetězce odesílaného do operace. Pojmenujte proměnnou `msg` a nastavte její typ **proměnné** na řetězec, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky, který ukazuje, jak přidat proměnnou.](./media/how-to-create-a-workflow-service-with-messaging-activities/add-variable-msg-string.jpg)  
  
     Opětovným kliknutím na tlačítko **proměnné** zavřete Editor proměnných.  
  
6. Klikněte na **definovat...** odkaz v textovém poli **obsah** v <xref:System.ServiceModel.Activities.Receive> aktivitě pro zobrazení dialogového okna **definice obsahu** Vyberte přepínač **parametry** , klikněte na odkaz **Přidat nový parametr** , do `inMsg` textového pole **název** zadejte text, v rozevíracím seznamu **typ** vyberte **řetězec** a zadejte `msg` do textového pole **přiřadit** , jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky, který ukazuje přidání obsahu parametrů](./media/how-to-create-a-workflow-service-with-messaging-activities/adding-parameters-content.jpg)  
  
     Tato možnost určuje, že aktivita Receive přijme parametr řetězce a že jsou data svázána s `msg` proměnnou. Kliknutím na tlačítko **OK** zavřete dialogové okno **definice obsahu** .  
  
7. Kliknutím na odkaz **definovat...** v poli **obsah** v <xref:System.ServiceModel.Activities.SendReply> aktivitě zobrazíte dialogové okno **definice obsahu** . Vyberte přepínač **parametry** , klikněte na odkaz **Přidat nový parametr** , zadejte do textového pole `outMsg` **název** , v rozevíracím seznamu **typ** vyberte **řetězec** a `msg` v textovém poli **hodnota** , jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky, který ukazuje, jak přidat parametr outMsg](./media/how-to-create-a-workflow-service-with-messaging-activities/outmsg-parameters-content.jpg)  
  
     Tato možnost určuje, že <xref:System.ServiceModel.Activities.SendReply> aktivita odesílá typ zprávy nebo kontraktu zprávy a že data jsou vázána na `msg` proměnnou. Vzhledem k tomu, že se jedná o <xref:System.ServiceModel.Activities.SendReply> aktivitu, znamená to, že data v nástroji `msg` slouží k naplnění zprávy, kterou aktivita odesílá zpátky klientovi. Kliknutím na tlačítko **OK** zavřete dialogové okno **definice obsahu** .  
  
8. Uložte a sestavte řešení kliknutím na nabídku **sestavení** a výběrem možnosti **Sestavit řešení**.  
  
## <a name="configure-the-workflow-service-project"></a>Konfigurace projektu služby pracovního postupu  
 Služba pracovního postupu je dokončená. V této části se dozvíte, jak nakonfigurovat řešení služby pracovního postupu, aby bylo možné ho snadno hostovat a spouštět. Toto řešení používá vývojový server ASP.NET k hostování služby.  
  
#### <a name="to-set-project-start-up-options"></a>Nastavení možností zahájení projektu  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem na **MyWFService** a vyberte **vlastnosti** . zobrazí se dialogové okno **Vlastnosti projektu** .  
  
2. Vyberte kartu **Web** a na stránce **zahájit akci** vyberte **konkrétní stránku** a zadejte `Service1.xamlx` text do textového pole, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky, který zobrazuje dialogové okno vlastností projektu.](./media/how-to-create-a-workflow-service-with-messaging-activities/project-properties-dialog.jpg)  
  
     Tato služba je hostitelem služby definované v Service1. xamlx na vývojovém serveru ASP.NET.  
  
3. Stisknutím kombinace kláves CTRL + F5 službu spusťte. Ikona vývojového serveru ASP.NET se zobrazí v pravé dolní části plochy, jak je znázorněno na následujícím obrázku.  
  
     ![Snímek obrazovky, který ukazuje ikonu serveru ASP.NET Developer Server.](./media/how-to-create-a-workflow-service-with-messaging-activities/asp-net-dev-server-icon.jpg)  
  
     Kromě toho Internet Explorer zobrazí stránku s nápovědu služby WCF pro danou službu.  
  
     ![Snímek obrazovky se stránkou s informacemi o službě WCF](./media/how-to-create-a-workflow-service-with-messaging-activities/wcf-service-help-page.jpg)  
  
4. Pokračujte k tématu [Postupy: přístup ke službě z aplikace pracovního postupu](how-to-access-a-service-from-a-workflow-application.md) k vytvoření klienta pracovního postupu, který volá tuto službu.  
  
## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](workflow-services.md)
- [Přehled hostování služeb pracovních postupů](hosting-workflow-services-overview.md)
- [Aktivity zasílání zpráv](messaging-activities.md)
