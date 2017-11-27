---
title: "Vytvoření dlouhodobé služby pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f4204de8c113c2ff553afec934b68f0beeb89580
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-long-running-workflow-service"></a>Vytvoření dlouhodobé služby pracovního postupu
Toto téma popisuje postup vytvoření dlouhodobé služby pracovního postupu. Dlouho běžící služeb pracovních postupů mohou spustit pro dlouhou dobu. V určitém okamžiku pracovní postup může se stát, nečinnosti čeká se na některé další informace. V takovém případě pracovního postupu uložena v databázi SQL a bude odebrán z paměti. Jakmile bude k dispozici další informace k instanci pracovního postupu je načteno zpět do paměti a pokračuje v provádění.  V tomto scénáři jsou implementace velmi zjednodušené řazení systému.  Klient odešle zprávu počáteční služby pracovního postupu spustit pořadí. Vrátí pořadí ID klienta. V tomto okamžiku služby pracovního postupu se čeká na další zprávu od klienta a klient se přepne do stavu nečinnosti a uložena v databázi systému SQL Server.  Když klient odešle na další zprávu pořadí položku, služby pracovního postupu je načteno zpět do paměti a dokončí zpracování pořadí. V ukázce kódu vrátí řetězec s informacemi o tom, že položka se přidal do pořadí. Ukázka kódu není určené jako aplikace skutečných technologie, ale spíš jednoduchý příklad, který znázorňuje dlouhotrvající služeb pracovních postupů. Toto téma předpokládá, že víte, jak vytvořit [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projekty a řešení.  
  
## <a name="prerequisites"></a>Požadavky  
 Musíte mít nainstalovaný pomocí tohoto průvodce použijte následující software:  
  
1.  Microsoft SQL Server 2008  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
3.  Microsoft[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
4.  Jste obeznámeni s použitím technologie WCF a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] a vědět, jak vytvářet projekty nebo řešení.  
  
### <a name="to-setup-the-sql-database"></a>K nastavení databáze SQL  
  
1.  V pořadí pro instance služby pracovního postupu na nastavit jako trvalý, musí mít nainstalovaný Microsoft SQL Server a je nutné nakonfigurovat databázi k ukládání instancí trvalou pracovních postupů. Spusťte Microsoft SQL Management Studio kliknutím **spustit** tlačítko výběru **všechny programy**, **Microsoft SQL Server 2008**, a **Microsoft SQL Management Studio**.  
  
2.  Klikněte **Connect** tlačítko a přihlaste se k instanci systému SQL Server  
  
3.  Klikněte pravým tlačítkem na **databáze** v zobrazení stromu a vyberte **nové databáze...** Chcete-li vytvořit novou databázi názvem `SQLPersistenceStore`.  
  
4.  Spusťte soubor skriptu SqlWorkflowInstanceStoreSchema.sql umístěný v adresáři C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en v databázi SQLPersistenceStore nastavit schémata potřebné databáze.  
  
5.  Spusťte soubor skriptu SqlWorkflowInstanceStoreLogic.sql umístěný v adresáři C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en v databázi SQLPersistenceStore nastavit logice potřebné databáze.  
  
### <a name="to-create-the-web-hosted-workflow-service"></a>Chcete-li vytvořit Web hostované služby pracovního postupu  
  
1.  Vytvořte prázdnou [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] řešení, pojmenujte ji `OrderProcessing`.  
  
2.  Přidejte nový [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projekt aplikace služby pracovního postupu s názvem `OrderService` k řešení.  
  
3.  V dialogovém okně Vlastnosti projektu, vyberte **webové** kartě.  
  
    1.  V části **spustit akci** vyberte **konkrétní stránky** a zadejte `Service1.xamlx`.  
  
         ![Vlastnosti webového projektu služby pracovního postupu](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")  
  
    2.  V části **servery** vyberte **použití místního webového serveru IIS**.  
  
         ![Nastavení místního webového serveru](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")  
  
        > [!WARNING]
        >  Je nutné spustit [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] v režimu správce, aby se toto nastavení.  
  
         Tyto dva kroky konfigurace projekt služby pracovního postupu, který má být hostované službou IIS.  
  
4.  Otevřete `Service1.xamlx` Pokud není již otevřete a odstranit existující **ReceiveRequest** a **SendResponse** aktivity.  
  
5.  Vyberte **sekvenční služby** aktivity a klikněte na tlačítko **proměnné** propojit a přidejte proměnné vidět na následujícím obrázku. Díky tomuto přidá některé proměnné, které se použijí později v rámci služby pracovního postupu.  
  
    > [!NOTE]
    >  Pokud CorrelationHandle v proměnné typu rozevíracího seznamu není, vyberte **Procházet pro typy** z rozevíracího seznamu. Zadejte CorrelationHandle v **název typu** CorrelationHandle vyberte ze seznamu a klikněte na tlačítko **OK**.  
  
     ![Přidání proměnné](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")  
  
6.  Přetáhnout myší **ReceiveAndSendReply** šablony aktivit do **sekvenční služby** aktivity. Tuto sadu aktivit, bude přijímat zprávu od klienta a odesílání odpovědí zpět.  
  
    1.  Vyberte **Receive** aktivity a sadu vlastností zvýrazněná na následujícím obrázku.  
  
         ![Sada přijímat vlastnosti aktivity](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")  
  
         Vlastnost DisplayName nastaví název zobrazený Receive aktivity v návrháři. Vlastnosti ServiceContractName a OperationName zadejte název kontraktu služby a operace, které jsou implementované pomocí aktivity Receive. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]použití kontraktů v pracovním postupu služeb najdete v tématu [použití kontraktů v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  
  
    2.  Klikněte **definovat...**  odkaz **ReceiveStartOrder** aktivity a nastavte vlastnosti zobrazené na následujícím obrázku.  Všimněte si, že **parametry** přepínače, parametr s názvem `p_customerName` je vázána `customerName` proměnné. Tím se nakonfiguruje **Receive** aktivity přijímat některá data a vytvoření vazby dat k lokální proměnné.  
  
         ![Nastavení dat přijatých aktivitou Receive](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")  
  
    3.  Vyberte **SendReplyToReceive** aktivity a nastavte vlastnost zvýrazněná vidět na následujícím obrázku.  
  
         ![Nastavení vlastností aktivity SendReply](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")  
  
    4.  Klikněte **definovat...**  odkaz **SendReplyToStartOrder** aktivity a nastavte vlastnosti zobrazené na následujícím obrázku. Všimněte si, že **parametry** přepínače; parametr s názvem `p_orderId` je vázána `orderId` proměnné. Toto nastavení určuje, že aktivita SendReplyToStartOrder vrátí hodnotu typu řetězec na volajícího.  
  
         ![Konfigurace obsahu data aktivit SendReply](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")  
  
    5.  Přetáhnout myší přiřadit aktivitu v rozmezí **Receive** a **SendReply** aktivity a nastavte vlastnosti, jak je znázorněno na následujícím obrázku:  
  
         ![Přidání aktivity přiřadit](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")  
  
         Tím se vytvoří nové ID pořadí a umístí hodnota proměnné orderId.  
  
    6.  Vyberte **ReplyToStartOrder** aktivity. V okně vlastností klikněte na tlačítko se třemi tečkami pro **CorrelationInitializers**. Vyberte **přidat inicializátoru** odkaz, zadejte `orderIdHandle` do textového pole inicializátoru vyberte inicializátoru korelace dotazu pro typ korelace a vyberte p_orderId pod rozevíracím dotazů XPATH. Tato nastavení znázorňuje následující obrázek. Click **OK**.  To inicializuje korelace mezi klientem a tuto instanci služby pracovního postupu. Když zprávu obsahující toto pořadí je přijata ID se směruje na tuto instanci služby pracovního postupu.  
  
         ![Přidání inicializátoru korelace](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")  
  
7.  Přetáhnout myší jiné **ReceiveAndSendReply** aktivity na konci pracovního postupu (mimo **pořadí** obsahující první **Receive** a  **SendReply** aktivit). To bude přijímat o druhou zprávu odesílaný klientem a reagovat na ni.  
  
    1.  Vyberte **pořadí** obsahující nově přidaný **Receive** a **SendReply** aktivit a klikněte na tlačítko **proměnné** tlačítko. Přidejte proměnnou vyznačené na následujícím obrázku:  
  
         ![Přidání nové proměnné](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")  
  
    2.  Vyberte **Receive** aktivity a nastavte vlastnosti zobrazené na následujícím obrázku:  
  
         ![Nastavit vlastnosti jsou Receive](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")  
  
    3.  Klikněte **definovat...**  na odkaz v **ReceiveAddItem** aktivity a přidání parametrů vidět na následujícím obrázku: tím se nakonfiguruje tak, aby přijímal dva parametry, kód a ID položky řazen aktivitu příjmu.  
  
         ![Určení parametrů pro druhý přijímat](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")  
  
    4.  Klikněte **CorrelateOn** třemi tečkami tlačítko a zadejte `orderIdHandle`. V části **dotazů XPath**, klikněte na šipku rozevíracího seznamu a vyberte `p_orderId`. Tím se nakonfiguruje korelaci na druhé stránce přijímat aktivity. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]korelace najdete [korelace](../../../../docs/framework/wcf/feature-details/correlation.md).  
  
         ![Nastavení vlastnosti CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")  
  
    5.  Přetáhnout myší **Pokud** aktivity ihned po **ReceiveAddItem** aktivity. Tato aktivita funguje stejně jako Pokud příkaz.  
  
        1.  Nastavte **podmínku** vlastnosti`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`  
  
        2.  Přetáhnout myší **přiřadit** aktivitu v **pak** části a druhý do **Else** oddíl nastavit vlastnosti **přiřadit** aktivity, jak je znázorněno na následujícím obrázku.  
  
             ![Přiřazení výsledek volání služby](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")  
  
             Pokud je podmínka vyhodnocena `true` **pak** části bude proveden. Pokud je podmínka vyhodnocena `false` **Else** části se spustí.  
  
        3.  Vyberte **SendReplyToReceive** aktivity a sady **DisplayName** vlastnost vidět na následujícím obrázku.  
  
             ![Nastavení vlastnosti aktivity SendReply](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")  
  
        4.  Klikněte **definovat...**  odkaz **SetReplyToAddItem** aktivity a nakonfigurovat ji, jak je znázorněno na následujícím obrázku. Tím se nakonfiguruje **SendReplyToAddItem** aktivitu pro vrácení hodnoty v `orderResult` proměnné.  
  
             ![Nastavení datové vazby pro aktivita SendReply](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")  
  
8.  Otevřete soubor web.config a přidejte následující prvky \<chování > části zapnout stálost pracovního postupu.  
  
    ```xml  
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />  
              <workflowIdle timeToUnload="0"/>  
    ```  
  
    > [!WARNING]
    >  Nezapomeňte nahradit hostitele a název instance systému SQL server v předchozím fragmentu kódu.  
  
9. Sestavte řešení.  
  
### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>Chcete-li vytvořit klientskou aplikaci, aby volání služby pracovního postupu  
  
1.  Přidat nový projekt konzolové aplikace volá `OrderClient` k řešení.  
  
2.  Odkazy na následující sestavení, které chcete přidat `OrderClient` projektu  
  
    1.  System.ServiceModel.dll  
  
    2.  System.ServiceModel.Activities.dll  
  
3.  Přidat odkaz na službu ve službě pracovní postup a zadejte `OrderService` jako obor názvů.  
  
4.  V `Main()` metoda klientského projektu přidejte následující kód:  
  
    ```  
    static void Main(string[] args)  
    {  
       // Send initial message to start the workflow service  
       Console.WriteLine("Sending start message");  
       StartOrderClient startProxy = new StartOrderClient();  
       string orderId = startProxy.StartOrder("Kim Abercrombie");  
  
       // The workflow service is now waiting for the second message to be sent  
       Console.WriteLine("Workflow service is idle...");  
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");  
       Console.ReadLine();  
  
       // Send the second message  
       Console.WriteLine("Sending add item message");  
       AddItemClient addProxy = new AddItemClient();  
       AddItem item = new AddItem();  
       item.p_itemId = "Zune HD";  
       item.p_orderId = orderId;  
  
       string orderResult = addProxy.AddItem(item);  
       Console.WriteLine("Service returned: " + orderResult);  
    }  
    ```  
  
5.  Sestavte řešení a spusťte `OrderClient` aplikace. Klient se zobrazí následující text:  
  
    ```Output  
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...  
    ```  
  
6.  Pokud chcete ověřit, že byl jako trvalý služby pracovního postupu, spustit SQL Server Management Studio přechodem na **spustit** nabídce zvolíte **všechny programy**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.  
  
    1.  V levém podokně rozbalte, **databáze**, **SQLPersistenceStore**, **zobrazení** a klikněte pravým tlačítkem na **System.Activities.DurableInstancing.Instances**  a vyberte **vyberte Top 1000 řádky**. V **výsledky** ověřte podokně se zobrazí alespoň jedna instance uvedené. Může mít další instance z předchozího spuštění během spuštění došlo k výjimce. Kliknutím pravým tlačítkem můžete odstranit stávající řádky **System.Activities.DurableInstancing.Instances** a výběrem **upravit Top 200 řádků**, stisknutí **Execute** tlačítko vyberete všechny řádky v podokně výsledků a vyberete **odstranit**.  Ověření instance, zobrazí se v databázi je instance aplikace vytvořena, ověřte zobrazení instance je prázdný před spuštěním klienta. Jakmile klient je spuštěné opětovným spuštěním dotazu (vyberte Top 1000 řádky) a ověřte přidaná novou instanci.  
  
7.  Stiskněte klávesu enter k odeslání zprávy přidat položku do služby pracovního postupu. Klient se zobrazí následující text:  
  
    ```Output  
    Sending add item messageService returned: Item added to orderPress any key to continue . . .  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
