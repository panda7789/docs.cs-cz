---
title: Vytvoření dlouhodobé služby pracovního postupu
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: ceda43cc41ceb3381b4700d6ea8b1871e368dccc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856202"
---
# <a name="creating-a-long-running-workflow-service"></a>Vytvoření dlouhodobé služby pracovního postupu

Toto téma popisuje, jak vytvořit dlouhodobě běžící službu pracovního postupu. Dlouhodobě běžící služby pracovních postupů můžou běžet dlouhou dobu. V určitém okamžiku může pracovní postup při čekání na některé další informace přejít na nečinné. V takovém případě je pracovní postup trvale uložen v databázi SQL a je odebrán z paměti. Když budou další informace k dispozici, instance pracovního postupu se načte zpátky do paměti a pokračuje v provádění.  V tomto scénáři implementujete velmi zjednodušený systém řazení.  Klient odešle počáteční zprávu službě pracovního postupu, aby zahájí objednávku. Vrátí klientovi ID objednávky. V tomto okamžiku služba pracovního postupu čeká na jinou zprávu od klienta a přejde do stavu nečinnosti a bude trvale uložena do databáze SQL Server.  Když klient pošle další zprávu pro objednání položky, služba pracovního postupu se načte zpátky do paměti a dokončí zpracování objednávky. V ukázce kódu vrátí řetězec oznamující, že položka byla přidána do objednávky. Ukázka kódu se nepovažuje za reálné použití technologie, ale spíše na jednoduchou ukázku, která znázorňuje dlouhodobě běžící služby pracovních postupů. Toto téma předpokládá, že máte v úmyslu vytvořit projekty a řešení sady Visual Studio 2012.

## <a name="prerequisites"></a>Požadavky

Pro použití tohoto Názorného postupu musíte mít nainstalovaný následující software:

1. Microsoft SQL Server 2008

2. Visual Studio 2012

3. Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]

4. Jste obeznámeni s WCF a sadou Visual Studio 2012 a víte, jak vytvářet projekty a řešení.

### <a name="to-setup-the-sql-database"></a>Nastavení SQL Database

1. Aby se instance služby pracovních postupů zachovaly, musíte mít nainstalovanou Microsoft SQL Server a musíte nakonfigurovat databázi tak, aby ukládala trvalé instance pracovního postupu. Spusťte Microsoft SQL Management Studio kliknutím na tlačítko **Start** , výběrem možnosti **všechny programy**, **Microsoft SQL Server 2008**a **Microsoft SQL Management Studio**.

2. Kliknutím na tlačítko **připojit** se přihlaste k instanci SQL Server.

3. Ve stromovém zobrazení klikněte pravým tlačítkem na **databáze** a vyberte **Nová databáze.** Vytvoří se nová databáze s názvem `SQLPersistenceStore`.

4. Spuštěním souboru skriptu SqlWorkflowInstanceStoreSchema. SQL umístěného v adresáři C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en v databázi SQLPersistenceStore nastavte potřebná schémata databáze.

5. Spusťte soubor skriptu SqlWorkflowInstanceStoreLogic. SQL umístěný v adresáři C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en v databázi SQLPersistenceStore a nastavte tak potřebnou databázovou logiku.

### <a name="to-create-the-web-hosted-workflow-service"></a>Vytvoření služby webového hostovaného pracovního postupu

1. Vytvořte prázdné řešení sady Visual Studio 2012 a pojmenujte ho `OrderProcessing`.

2. Přidejte do řešení nový projekt aplikace služby pracovního postupu `OrderService` WCF s názvem.

3. V dialogovém okně Vlastnosti projektu vyberte kartu **Web** .

    1. V části **Spustit akci** vyberte **konkrétní stránka** a `Service1.xamlx`zadejte.

        ![Webové vlastnosti projektu služby pracovního postupu](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Vytvořit možnost stránky pro web hostovaný pracovní postup – konkrétní služba")

    2. V části **servery** vyberte **použít místní webový server služby IIS**.

        ![Nastavení místního webového serveru](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Vytvoření služby Web Hosted Workflow Service – použijte možnost místní webový server služby IIS")

        > [!WARNING]
        > Chcete-li nastavit toto nastavení, je nutné spustit aplikaci Visual Studio 2012 v režimu správce.

        Tyto dva kroky nakonfigurují projekt služby pracovního postupu tak, aby byl hostovaný službou IIS.

4. Otevřete `Service1.xamlx` , pokud už není otevřený, a odstraňte existující aktivity **ReceiveRequest** a **SendResponse** .

5. Vyberte aktivitu **sekvenční služby** a klikněte na odkaz **proměnné** a přidejte proměnné zobrazené na následujícím obrázku. Tím se přidají některé proměnné, které se použijí později ve službě pracovního postupu.

    > [!NOTE]
    > Pokud popisovač CorrelationHandle není v rozevíracím seznamu typ proměnné, vyberte **Vyhledat typy** z rozevírací nabídky. Do pole **název typu** zadejte popisovač CorrelationHandle, v seznamu vyberte popisovač CorrelationHandle a klikněte na **OK**.

    ![Přidat proměnné](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Přidejte proměnné do aktivity sekvenční služby.")

6. Přetáhněte šablonu aktivity **ReceiveAndSendReply** do aktivity **sekvenční služby** . Tato sada aktivit obdrží zprávu od klienta a pošle odpověď zpátky.

    1. Vyberte aktivitu **přijmout** a nastavte vlastnosti zvýrazněné na následujícím obrázku.

        ![Nastavit vlastnosti aktivity Receive](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Nastavte vlastnosti aktivity Receive.")

        Vlastnost DisplayName nastaví název zobrazený pro aktivitu Receive v návrháři. Vlastnosti ServiceContractName a OperationName určují název kontraktu služby a operace, které jsou implementované aktivitou Receive. Další informace o tom, jak se ve službách pracovních postupů používají kontrakty, najdete v tématu [Použití kontraktů v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).

    2. Klikněte na odkaz **definovat...** v aktivitě **ReceiveStartOrder** a nastavte vlastnosti zobrazené na následujícím obrázku.  Všimněte si, že přepínač **Parameters** je vybrán, parametr s názvem `p_customerName` `customerName` je vázán na proměnnou. Tím se nakonfiguruje aktivita **příjmu** pro příjem některých dat a vazba těchto dat na lokální proměnné.

        ![Nastavení dat přijatých aktivitou Receive](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Nastavte vlastnosti pro data přijatá aktivitou Receive.")

    3. Vyberte aktivitu **SendReplyToReceive** a nastavte zvýrazněnou vlastnost, která je znázorněna na následujícím obrázku.

        ![Nastavení vlastností aktivity SendReply](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")

    4. Klikněte na odkaz **definovat...** v aktivitě **SendReplyToStartOrder** a nastavte vlastnosti zobrazené na následujícím obrázku. Všimněte si, že přepínač **Parameters** je vybrán; parametr s názvem `p_orderId` je vázán `orderId` na proměnnou. Toto nastavení určuje, že aktivita SendReplyToStartOrder vrátí hodnotu typu String volajícímu.

        ![Konfigurace dat obsahu aktivity SendReply](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Nakonfigurujte nastavení pro aktivitu SetReplyToStartOrder.")

    5. Přetáhněte aktivitu přiřadit mezi aktivitami **Receive** a **SendReply** a nastavte vlastnosti tak, jak je znázorněno na následujícím obrázku:

        ![Přidání aktivity přiřazení](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Přidejte aktivitu přiřazení.")

        Tím se vytvoří nové ID objednávky a hodnota se umístí do proměnné ČísloObjednávky.

    6. Vyberte aktivitu **ReplyToStartOrder** . V okně Vlastnosti klikněte na tlačítko se třemi tečkami pro **inicializátoři CorrelationInitializers**. Vyberte odkaz **Přidat inicializátor** , do textového `orderIdHandle` pole inicializátor zadejte, pro typ korelace vyberte inicializátor korelace a v rozevíracím seznamu dotazy XPath vyberte p_orderId. Tato nastavení jsou znázorněna na následujícím obrázku. Klikněte na **OK**.  Tím se inicializuje korelace mezi klientem a touto instancí služby pracovního postupu. Když se přijme zpráva obsahující toto ID objednávky, je směrována do této instance služby pracovního postupu.

        ![Přidání inicializátoru korelace](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Přidejte inicializátor korelace.")

7. Přetáhněte další aktivitu **ReceiveAndSendReply** na konec pracovního postupu (mimo **sekvenci** obsahující první aktivity **Receive** a **SendReply** ). Tím přijde druhá zpráva odeslaná klientem a reaguje na ni.

    1. Vyberte **sekvenci** , která obsahuje nově přidané aktivity **Receive** a **SendReply** a klikněte na tlačítko **proměnné** . Přidejte proměnnou zvýrazněnou na následujícím obrázku:

        ![Přidávání nových proměnných](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Přidejte proměnnou ItemID.")

        Do `Sequence` oboru `orderResult` přidejte také **řetězec** as.

    2. Vyberte aktivitu **Receive** a nastavte vlastnosti zobrazené na následujícím obrázku:

        ![Nastavit vlastnosti aktivity Receive](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Nastavte vlastnosti aktivity Receive.")

        > [!NOTE]
        > Nezapomeňte změnit pole **ServiceContractName** pomocí `../IAddItem`.

    3. Klikněte na odkaz **definovat...** v aktivitě **ReceiveAddItem** a přidejte parametry zobrazené na následujícím obrázku: tím se nakonfiguruje aktivita Receive pro příjem dvou parametrů, ID objednávky a ID položky, která je seřazená.

        ![Určení parametrů pro druhý příjem](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Nakonfigurujte aktivitu Receive pro příjem dvou parametrů.")

    4. Klikněte na tlačítko se třemi tečkami `orderIdHandle`CorrelateOn a zadejte. V části **dotazy XPath**klikněte na šipku rozevíracího seznamu a `p_orderId`vyberte. Tím se nakonfiguruje korelace pro druhou aktivitu Receive. Další informace o korelaci najdete v tématu [korelace](../../../../docs/framework/wcf/feature-details/correlation.md).

        ![Nastavení vlastnosti vlastnosti CorrelatesOn](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Nastavte vlastnost vlastnosti CorrelatesOn.")

    5. Přetáhněte aktivitu **if** hned za aktivitu **ReceiveAddItem** . Tato aktivita funguje stejně jako příkaz if.

        1. Nastavte vlastnost **Condition** na`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`

        2. Přetáhněte aktivitu **přiřadit** v části do oddílu **then** a jinou do části **Else** nastavte vlastnosti aktivity **přiřazení** , jak je znázorněno na následujícím obrázku.

            ![Přiřazuje se výsledek volání služby] . (./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Přiřaďte výsledek volání služby.")

            Pokud je `true` podmínka, bude provedena v oddílu **then** . Pokud je podmínka `false` v části **Else** , je provedena.

        3. Vyberte aktivitu **SendReplyToReceive** a nastavte vlastnost **DisplayName** znázorněnou na následujícím obrázku.

            ![Nastavení vlastností aktivity SendReply](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Nastavte vlastnost aktivity SendReply.")

        4. Klikněte na odkaz **definovat...** v aktivitě **SetReplyToAddItem** a nakonfigurujte ho tak, jak je znázorněno na následujícím obrázku. Tím se nakonfiguruje aktivita **SendReplyToAddItem** , která vrátí hodnotu v `orderResult` proměnné.

            ![Nastavení datové vazby pro aktivitu SendReply](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Nastaví vlastnost pro aktivitu SendReplyToAddItem.")

8. Otevřete soubor Web. config a přidejte následující prvky do \<oddílu chování >, aby bylo možné povolit trvalost pracovního postupu.

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    > Nezapomeňte nahradit název hostitele a instance serveru SQL Server v předchozím fragmentu kódu.

9. Sestavte řešení.

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>Vytvoření klientské aplikace pro volání služby pracovního postupu

1. Přidejte do řešení nový projekt konzolové `OrderClient` aplikace s názvem.

2. Přidat do `OrderClient` projektu odkazy na následující sestavení

    1. System.ServiceModel.dll

    2. System.ServiceModel.Activities.dll

3. Přidejte do služby pracovního postupu odkaz na službu a jako `OrderService` obor názvů zadejte.

4. `Main()` V metodě klientského projektu přidejte následující kód:

    ```csharp
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

5. Sestavte řešení a spusťte `OrderClient` aplikaci. Klient zobrazí následující text:

    ```output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. Chcete-li ověřit, zda byla služba pracovního postupu trvalá, spusťte SQL Server Management Studio přejděte do nabídky **Start** a vyberte možnost **všechny programy** **Microsoft SQL Server 2008** **SQL Server Management Studio**.

    1. V levém podokně rozbalte, **databáze**, **SQLPersistenceStore**, **zobrazení** a klikněte pravým tlačítkem na **System. Activities. DurableInstancing. Instances** a vyberte **Vybrat prvních 1000 řádků**. V podokně **výsledků** ověřte, že je v seznamu uvedena alespoň jedna instance. Pokud při spuštění dojde k výjimce, může dojít k dalším instancím z předchozích spuštění. Existující řádky můžete odstranit tak, že kliknete pravým tlačítkem na **System. Activities. DurableInstancing. Instances** a vyberete **Upravit horní 200 řádků**, stisknete tlačítko **Spustit** , vyberete všechny řádky v podokně výsledků a vyberete **Odstranit**.  Chcete-li ověřit, zda je instance zobrazená v databázi instancí aplikace vytvořená, ověřte, zda je zobrazení instance před spuštěním klienta prázdné. Po spuštění klienta znovu spusťte dotaz (vyberte horní 1000 řádků) a ověřte, zda byla přidána nová instance.

7. Stisknutím klávesy ENTER odešlete zprávu přidat položku do služby pracovního postupu. Klient zobrazí následující text:

    ```output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a>Viz také:

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
