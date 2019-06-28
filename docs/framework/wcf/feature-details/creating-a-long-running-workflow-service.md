---
title: Vytvoření dlouhodobé služby pracovního postupu
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 1ca0f2ed4c2ab900191165d100848811e5436c3c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425410"
---
# <a name="creating-a-long-running-workflow-service"></a>Vytvoření dlouhodobé služby pracovního postupu
Toto téma popisuje postup vytvoření dlouhodobé služby pracovního postupu. Dlouho běžící pracovní postup služby může spuštění pro dlouhou dobu. V určitém okamžiku může přejít pracovního postupu nečinnosti čekání na určité další informace. V takovém případě pracovního postupu se ukládají do databáze SQL a bude odebrán z paměti. Jakmile je k dispozici další informace o instanci pracovního postupu je načten do paměti a pokračuje v provádění.  V tomto scénáři při implementaci velmi zjednodušený pořadí systému.  Klient odešle zprávu počáteční spouštění pořadí služby pracovního postupu. Vrátí ID objednávky do klienta. V tomto okamžiku Služba pracovního postupu je čekání na další zprávu od klienta a přejde do stavu nečinnosti a se ukládají do databáze SQL serveru.  Když klient odešle na další zprávu pro objednávky položku, služba pracovního postupu je načten do paměti a ukončí zpracování objednávky. Ve vzorovém kódu vrátí řetězec s informacemi o tom, že položka se přidala pořadí. Vzorový kód neměl být reálné aplikaci technologie, ale spíše jednoduchý příklad, který znázorňuje dlouhodobé služby pracovního postupu. Toto téma předpokládá, že víte, jak vytvořit řešení a projekty Visual Studio 2012.

## <a name="prerequisites"></a>Požadavky
 Musíte mít nainstalovaný pomocí tohoto průvodce použijte následující software:

1. Microsoft SQL Server 2008

2. Visual Studio 2012

3. Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]

4. Jste obeznámeni s WCF a Visual Studio 2012 a vědět, jak vytvořit projekty a řešení.

### <a name="to-setup-the-sql-database"></a>Nastavení databáze SQL

1. V pořadí pro instance služby pracovního postupu chcete nastavit jako trvalý, musí mít nainstalovaný Microsoft SQL Server a je nutné nakonfigurovat databázi k ukládání instancí trvalá pracovního postupu. Microsoft SQL Management Studio spusťte kliknutím **Start** tlačítka, výběr **všechny programy**, **Microsoft SQL Server 2008**, a **Microsoft SQL Management Studio**.

2. Klikněte na tlačítko **připojit** tlačítko pro přihlášení k instanci systému SQL Server

3. Klikněte pravým tlačítkem myši **databází** ve stromovém zobrazení a vyberte **novou databázi...** Chcete-li vytvořit novou databázi s názvem `SQLPersistenceStore`.

4. Spuštění souboru skriptu SqlWorkflowInstanceStoreSchema.sql nachází v adresáři C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en SQLPersistenceStore databázi nastavit potřebné databázová schémata.

5. Spuštění souboru skriptu SqlWorkflowInstanceStoreLogic.sql nachází v adresáři C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en SQLPersistenceStore databázi nastavit logiky potřebné databáze.

### <a name="to-create-the-web-hosted-workflow-service"></a>Vytvoření webu hostované služby pracovního postupu

1. Vytvoření prázdného řešení sady Visual Studio 2012, pojmenujte ho `OrderProcessing`.

2. Přidat nový projekt aplikace služby pracovního postupu WCF s názvem `OrderService` do řešení.

3. V dialogovém okně Vlastnosti projektu, vyberte **webové** kartu.

    1. V části **spustit akci** vyberte **konkrétní stránka** a určete `Service1.xamlx`.

         ![Vlastnosti webového projektu pracovního postupu služby](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "vytvoření služby pracovního postupu hostovaná na webu – možnost konkrétní stránky")

    2. V části **servery** vyberte **použití místního webového serveru IIS**.

         ![Místní nastavení webového serveru](./media/creating-a-long-running-workflow-service/use-local-web-server.png "vytvoření služby pracovního postupu hostovaná na webu – možnost použití místního webového serveru IIS")

        > [!WARNING]
        >  V režimu správce, aby toto nastavení je nutné spustit sadu Visual Studio 2012.

         Tyto dva kroky konfigurace projektu pracovního postupu služby hostované službou IIS.

4. Otevřete `Service1.xamlx` Pokud to není již otevřete a odstranit existující **ReceiveRequest** a **SendResponse** aktivity.

5. Vyberte **sekvenční služba** aktivity a kliknutím **proměnné** propojit a přidejte proměnné je znázorněno na následujícím obrázku. To přidá několik proměnných, které se použijí později ve službě pracovního postupu.

    > [!NOTE]
    >  Pokud rutiny CorrelationHandle není v rozevíracím seznamu Typ proměnné, vyberte **vyhledat typy** z rozevíracího seznamu. Zadejte rutiny CorrelationHandle v **název typu** pole, vyberte rutiny CorrelationHandle ze seznamu a klikněte na tlačítko **OK**.

     ![Přidejte proměnné](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "přidejte proměnné do aktivity sekvenční služba.")

6. Přetáhnout myší **ReceiveAndSendReply** šablona aktivity do **sekvenční služba** aktivity. Tuto sadu aktivity bude přijímat zprávy z klienta a odeslat zpět odpověď.

    1. Vyberte **Receive** aktivity a nastavte vlastnosti zvýrazněný na následujícím obrázku.

         ![Zobrazí vlastnosti aktivity nastavit](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "nastavit vlastnosti aktivity Receive.")

         Vlastnost DisplayName nastaví název zobrazený pro aktivitu příjmu v návrháři. Vlastnosti ServiceContractName a OperationName zadejte název kontraktu služby a operace, které jsou implementovány pomocí aktivity Receive. Další informace o používání smluv ve službách pracovních postupů v tématu [použití kontraktů v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).

    2. Klikněte na tlačítko **definovat...**  propojit **ReceiveStartOrder** aktivity a nastavte vlastnosti zobrazené na následujícím obrázku.  Všimněte si, že **parametry** je přepínač vybrán, parametr s názvem `p_customerName` je vázán `customerName` proměnné. Tím se nakonfiguruje **Receive** aktivity přijímají nějaká data, a tato data svázat lokální proměnné.

         ![Nastavení data byla přijata aktivita Receive](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "nastavit vlastnosti pro data byla přijata aktivita Receive.")

    3. Vyberte **SendReplyToReceive** aktivity a nastavte vlastnost zvýrazněné je znázorněno na následujícím obrázku.

         ![Nastavení vlastností pro aktivitu odeslání odpovědi SendReply](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")

    4. Klikněte na tlačítko **definovat...**  propojit **SendReplyToStartOrder** aktivity a nastavte vlastnosti zobrazené na následujícím obrázku. Všimněte si, že **parametry** je přepínač vybrán; parametr s názvem `p_orderId` je vázán `orderId` proměnné. Toto nastavení určuje, že aktivita SendReplyToStartOrder vrátí hodnotu typu String volajícímu.

         ![Konfigurace obsahu dat aktivitu odeslání odpovědi SendReply](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "nakonfigurovat nastavení pro SetReplyToStartOrder aktivitu.")

    5. Přetažení aktivity přiřazení mezi **Receive** a **odeslání odpovědi SendReply** aktivity a nastavte vlastnosti, jak je znázorněno na následujícím obrázku:

         ![Přidání aktivity přiřadit](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "přidat aktivitu přiřazení.")

         Tím se vytvoří nové ID objednávky a umístí hodnota v proměnné orderId.

    6. Vyberte **ReplyToStartOrder** aktivity. V okně Vlastnosti klikněte na tlačítko se třemi tečkami pro **correlationinitializers uveden**. Vyberte **přidat inicializační výraz** propojení, zadejte `orderIdHandle` v textovém poli inicializátor vyberte inicializátor korelace dotazu pro typ korelace a vyberte p_orderId v rozevíracím seznamu dotazy XPATH. Tato nastavení znázorňuje následující obrázek. Klikněte na **OK**.  To inicializuje korelaci mezi klientem a tato instance služby pracovního postupu. Když zprávu obsahující tuto objednávku přijata ID se rozšíří do této instance služby pracovního postupu.

         ![Přidání inicializátor korelace](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "přidat inicializátor korelace.")

7. Přetáhnout myší jiného **ReceiveAndSendReply** aktivity na konci pracovního postupu (mimo **pořadí** obsahující první **Receive** a  **Odeslání odpovědi SendReply** aktivit). To se druhá zpráva zaslanou klientem a reagovat na něj.

    1. Vyberte **pořadí** , která obsahuje nově přidaný **Receive** a **odeslání odpovědi SendReply** aktivit a klikněte na tlačítko **proměnné** tlačítko. Přidejte proměnnou zvýrazněný na následujícím obrázku:

         ![Přidání nové proměnné](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "ItemId proměnné přidejte.")
         
         Přidejte také `orderResult` jako **řetězec** v `Sequence` oboru.

    2. Vyberte **Receive** aktivity a nastavte vlastnosti zobrazené na následujícím obrázku:

         ![Nastavit vlastnosti aktivity Receive](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "nastavit vlastnosti aktivity Receive.")
         
         > [!NOTE]
         >  Nezapomeňte změnit **ServiceContractName** pole `../IAddItem`.

    3. Klikněte na tlačítko **definovat...**  propojit **ReceiveAddItem** aktivity a přidat parametry je znázorněno na následujícím obrázku: tím se nakonfiguruje tak, aby přijímal dva parametry, ID objednávky a ID položky, seřadí se aktivita receive.

         ![Zadání parametrů pro druhý receive](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "konfigurace aktivity receive přijímat dva parametry.")

    4. Klikněte na tlačítko **CorrelateOn** tlačítko se třemi tečkami tlačítko a zadejte `orderIdHandle`. V části **dotazy XPath**, klikněte na šipku rozevíracího seznamu a vyberte `p_orderId`. Tím se nakonfiguruje korelace v druhém aktivita příjmu. Další informace o korelaci naleznete v tématu [korelace](../../../../docs/framework/wcf/feature-details/correlation.md).

         ![Nastavení vlastnosti vlastnosti CorrelatesOn](./media/creating-a-long-running-workflow-service/correlateson-setting.png "vlastnosti CorrelatesOn vlastnost nastavit.")

    5. Přetáhnout myší **Pokud** aktivity ihned po **ReceiveAddItem** aktivity. Tato aktivita funguje stejně jako if – příkaz.

        1. Nastavte **podmínku** vlastnost `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`

        2. Přetáhnout myší **přiřadit** aktivitu v **pak** oddílu a druhý do **Else** části nastavit vlastnosti **přiřadit** aktivity, jak je znázorněno na následujícím obrázku.

             ![Přiřazení na výsledek volání služby](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "přiřadit výsledek volání služby.")

             Pokud je podmínka `true` **pak** oddílu se spustí. Pokud je podmínka `false` **Else** část je spuštěna.

        3. Vyberte **SendReplyToReceive** aktivity a nastavte **DisplayName** vlastnost je znázorněno na následujícím obrázku.

             ![Nastavení vlastností aktivitu odeslání odpovědi SendReply](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "nastavit vlastnost aktivity SendReply.")

        4. Klikněte na tlačítko **definovat...**  propojit **SetReplyToAddItem** aktivity a nakonfigurujte, jak je znázorněno na následujícím obrázku. Tím se nakonfiguruje **SendReplyToAddItem** aktivity k vrácení hodnoty v `orderResult` proměnné.

             ![Nastavení datové vazby pro aktivitu odeslání odpovědi SendReply](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "nastavit vlastnost aktivity SendReplyToAddItem.")

8. Otevřete soubor web.config a přidat následující prvky \<chování > části Povolit trvalost pracovního postupu.

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    >  Nezapomeňte nahradit hostitele a název instance systému SQL server v předchozím fragmentu kódu.

9. Sestavte řešení.

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>Chcete-li vytvořit klientskou aplikaci k volání služby pracovního postupu

1. Přidat nový projekt konzolové aplikace volá `OrderClient` do řešení.

2. Přidat odkazy na následující sestavení, které chcete `OrderClient` projektu

    1. System.ServiceModel.dll

    2. System.ServiceModel.Activities.dll

3. Přidání odkazu na službu ve službě pracovního postupu a určete `OrderService` jako obor názvů.

4. V `Main()` metoda klientský projekt, přidejte následující kód:

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

5. Sestavte řešení a spustit `OrderClient` aplikace. Klient se zobrazí následující text:

    ```Output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. Pokud chcete ověřit, že služba pracovního postupu byla trvale uložena, spustit SQL Server Management Studio tak, že přejdete **Start** nabídky, výběr **všechny programy**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.

    1. V levém podokně rozbalte, **databází**, **SQLPersistenceStore**, **zobrazení** klikněte pravým tlačítkem myši **System.Activities.DurableInstancing.Instances**  a vyberte **vybrat prvních 1000 řádků**. V **výsledky** podokně ověření se zobrazí alespoň jednu instanci. Mohou existovat další instance z předchozího spuštění Pokud během spuštění došlo k výjimce. Kliknutím pravým tlačítkem můžete odstranit existující řádky **System.Activities.DurableInstancing.Instances** a vyberete **upravit 200 horní řádky**, stisknutí **Execute** tlačítko, Výběr všech řádků v podokně výsledků a vyberete **odstranit**.  K ověření instance, zobrazí se v databázi je instance aplikace vytvořena, ověřte zobrazení instancí je prázdná před spuštěním klienta. Jakmile klient je spuštěný spusťte znovu dotaz (vybrat prvních 1000 řádků) a ověřte novou instanci se přidala.

7. Stiskněte klávesu enter k odeslání zprávy přidat položky do služby pracovního postupu. Klient se zobrazí následující text:

    ```Output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a>Viz také:

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
