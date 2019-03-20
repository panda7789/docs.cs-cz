---
title: Tok transakcí do služeb pracovních postupů a mimo ně
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 272e188b448864450621665f80ea0ab8b0037b37
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185685"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Tok transakcí do služeb pracovních postupů a mimo ně
Služby pracovních postupů a klienti mohou účastnit transakce.  Operace služeb se stanou součástí okolí transakce, umístěte <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. Všechna volání prováděných <xref:System.ServiceModel.Activities.Send> nebo <xref:System.ServiceModel.Activities.SendReply> aktivitu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> bude také možné v rámci ambientní transakce. Klientská aplikace pracovního postupu můžete vytvořit pomocí okolí transakce <xref:System.Activities.Statements.TransactionScope> aktivity a volání operací služby pomocí okolí transakce. Toto téma vás provede procesem vytvoření služby pracovních postupů a pracovních postupů klienta, který se podílet na transakcích.  
  
> [!WARNING]
>  Pokud instance služby pracovního postupu je načten v rámci transakce a obsahuje pracovní postup <xref:System.Activities.Statements.Persist> aktivity, instance pracovního postupu se zablokuje, dokud nebude transakce vyprší časový limit.  
  
> [!IMPORTANT]
>  Vždy, když použijete <xref:System.ServiceModel.Activities.TransactedReceiveScope> doporučujeme umístit všechny přijme v pracovním postupu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.  
  
> [!IMPORTANT]
>  Při použití <xref:System.ServiceModel.Activities.TransactedReceiveScope> a doručování zpráv v nesprávném pořadí, pracovní postup přeruší se při pokusu doručit první zprávu mimo pořadí. Můžete třeba Ujistěte se, že váš pracovní postup je vždy na konzistentního koncový bod při pracovního postupu nečinné po dlouhou dobu. To vám umožní restartovat pracovní postup z předchozího bodu trvalosti by měl pracovní postup přeruší.  
  
### <a name="create-a-shared-library"></a>Vytvořte sdílenou knihovnu  
  
1.  Vytvoření nové prázdné řešení sady Visual Studio.  
  
2.  Přidat nový projekt knihovny tříd s názvem `Common`. Přidejte odkazy na následující sestavení:  
  
    -   System.Activities.dll  
  
    -   System.ServiceModel.dll  
  
    -   System.ServiceModel.Activities.dll  
  
    -   System.Transactions.dll  
  
3.  Přidejte novou třídu s názvem `PrintTransactionInfo` k `Common` projektu. Tato třída je odvozena z <xref:System.Activities.NativeActivity> a přetížení <xref:System.Activities.NativeActivity.Execute%2A> metody.  
  
    ```  
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     Toto je nativní aktivitu, která zobrazí informace o okolí transakce a používá se v pracovních postupech služby a klient používat v tomto tématu. Sestavte řešení, které chcete zpřístupnit tuto aktivitu v **běžné** část **nástrojů**.  
  
### <a name="implement-the-workflow-service"></a>Implementace služby pracovního postupu  
  
1.  Přidejte novou službu pracovního postupu WCF volá `WorkflowService` k `Common` projektu. Klikněte na tlačítko vpravo `Common` projekt, vyberte **přidat**, **novou položku...** Vyberte **pracovního postupu** pod **nainstalované šablony** a vyberte **služby pracovního postupu WCF**.  
  
     ![Přidání služby pracovních postupů](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2.  Odstranit výchozí `ReceiveRequest` a `SendResponse` aktivity.  
  
3.  Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivitu `Sequential Service` aktivity. Nastavte vlastnost text na `"Workflow Service starting ..."` jak je znázorněno v následujícím příkladu.  
  
     ! [Přidání aktivity WriteLine activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg) sekvenční služba  
  
4.  Přetáhnout myší <xref:System.ServiceModel.Activities.TransactedReceiveScope> po <xref:System.Activities.Statements.WriteLine> aktivity. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivit najdete v **zasílání zpráv** část **nástrojů**. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivity se skládá ze dvou částí **žádosti** a **tělo**. **Žádosti** oddíl obsahuje <xref:System.ServiceModel.Activities.Receive> aktivity. **Tělo** oddíl obsahuje aktivity ke spuštění v rámci transakce po byla přijata zpráva.  
  
     ![Přidání aktivity TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5.  Vyberte <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity a kliknutím **proměnné** tlačítko. Přidejte následující proměnné.  
  
     ![Přidávání proměnných do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    >  Můžete odstranit datovou proměnnou, která je k dispozici ve výchozím nastavení. Můžete také použít existující proměnnou popisovač.  
  
6.  Přetáhnout myší <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci **žádosti** část <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. Nastavte následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |CanCreateInstance|True (zaškrtávací políčko)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Pracovní postup by měl vypadat nějak takto:  
  
     ![Přidání aktivity Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7.  Klikněte na tlačítko **definovat...**  propojit <xref:System.ServiceModel.Activities.Receive> aktivity a proveďte následující nastavení:  
  
     ![Nastavení zpráv aktivity Receive](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8.  Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity do těla oddílu <xref:System.ServiceModel.Activities.TransactedReceiveScope>. V rámci <xref:System.Activities.Statements.Sequence> aktivity přetáhnout myší dvě <xref:System.Activities.Statements.WriteLine> aktivity a nastavte <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnosti, jak je znázorněno v následující tabulce.  
  
    |Aktivita|Hodnota|  
    |--------------|-----------|  
    |1. WriteLine|"Service: Zobrazit dokončené"|  
    |2. WriteLine|"Service: Přijata = "+ requestMessage|  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Pořadí po přidání aktivity WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Přetáhnout myší `PrintTransactionInfo` aktivitu po druhé <xref:System.Activities.Statements.WriteLine> aktivity v **tělo** v <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.  
  
     ![Po přidání PrintTransactionInfo pořadí](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Přetáhnout myší <xref:System.Activities.Statements.Assign> aktivity po `PrintTransactionInfo` aktivity a nastavte jeho vlastnosti podle následující tabulky.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |Chcete-li|replyMessage|  
    |Hodnota|"Service: Odeslání odpovědi."|  
  
11. Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po <xref:System.Activities.Statements.Assign> aktivity a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Service: Začněte odpověď."  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Po přidání přiřadit a WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Klikněte pravým tlačítkem myši <xref:System.ServiceModel.Activities.Receive> aktivitu a vyberte **vytvořit odeslání odpovědi SendReply** a vložte za poslední <xref:System.Activities.Statements.WriteLine> aktivity. Klikněte na tlačítko **definovat...**  propojit `SendReplyToReceive` aktivity a proveďte následující nastavení.  
  
     ![Nastavení zpráva odpovědi](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po `SendReplyToReceive` aktivity a nastavte má <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Service: Byla odeslána odpověď."  
  
14. Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity v dolní části pracovního postupu a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Service: Pracovní postup skončí, stisknutím klávesy ENTER ukončete."  
  
     Pracovní postup dokončený služby by měl vypadat nějak takto:  
  
     ![Dokončení pracovního postupu služby](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Implementace klienta pracovního postupu  
  
1.  Přidat novou aplikaci pracovního postupu WCF, s názvem `WorkflowClient` k `Common` projektu. Klikněte na tlačítko vpravo `Common` projekt, vyberte **přidat**, **novou položku...** Vyberte **pracovního postupu** pod **nainstalované šablony** a vyberte **aktivity**.  
  
     ![Přidání aktivity projektu](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2.  Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity na návrhovou plochu.  
  
3.  V rámci <xref:System.Activities.Statements.Sequence> přetáhnout aktivity <xref:System.Activities.Statements.WriteLine> aktivity a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost `"Client: Workflow starting"`. Pracovní postup by teď měl vypadat takto:  
  
     ![Přidání aktivity WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4.  Přetáhnout myší <xref:System.Activities.Statements.TransactionScope> aktivity po <xref:System.Activities.Statements.WriteLine> aktivity.  Vyberte <xref:System.Activities.Statements.TransactionScope> aktivity, klikněte na tlačítko proměnné a přidejte následující proměnné.  
  
     ![Přidejte proměnné do objektu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5.  Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity do textu <xref:System.Activities.Statements.TransactionScope> aktivity.  
  
6.  Přetáhnout myší `PrintTransactionInfo` aktivitu v rámci <xref:System.Activities.Statements.Sequence>  
  
7.  Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po `PrintTransactionInfo` aktivity a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "klienta: Od odeslání". Pracovní postup by teď měl vypadat takto:  
  
     ![Přidání klienta: Od aktivity odesílání](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8.  Přetáhnout myší <xref:System.ServiceModel.Activities.Send> aktivity po <xref:System.Activities.Statements.Assign> aktivity a nastavte následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Nastavení vlastnosti aktivity Send](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Klikněte na tlačítko **definovat...**  odkaz a proveďte následující nastavení:  
  
     ![Odeslání zprávy nastavení aktivity](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Klikněte pravým tlačítkem myši <xref:System.ServiceModel.Activities.Send> aktivitu a vyberte **vytvořit ReceiveReply**. <xref:System.ServiceModel.Activities.ReceiveReply> Aktivity se automaticky umístí po <xref:System.ServiceModel.Activities.Send> aktivity.  
  
11. Klikněte na tlačítko... definovat odkaz na aktivitu ReceiveReplyForSend a proveďte následující nastavení:  
  
     ![Nastavení ReceiveForSend zprávy](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity mezi <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "klienta: Odeslat kompletní."  
  
13. Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po <xref:System.ServiceModel.Activities.ReceiveReply> aktivity a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "na straně klienta: Přijatá odpověď = "+ replyMessage  
  
14. Přetáhnout myší `PrintTransactionInfo` aktivity po <xref:System.Activities.Statements.WriteLine> aktivity.  
  
15. Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity na konci pracovního postupu a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Klienta pracovní postup ukončen." Pracovní postup dokončený klienta by mělo vypadat jako na následujícím diagramu.  
  
     ![Workfliow dokončené klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Sestavte řešení.  
  
### <a name="create-the-service-application"></a>Vytvoření aplikace služby  
  
1.  Přidat nový projekt konzolové aplikace s názvem `Service` do řešení. Přidejte odkazy na následující sestavení:  
  
    1.  System.Activities.dll  
  
    2.  System.ServiceModel.dll  
  
    3.  System.ServiceModel.Activities.dll  
  
2.  Otevřete vygenerovaný soubor Program.cs a následující kód:  
  
    ```  
    static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {                
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };         
          }  
    ```  
  
3.  Následující soubor app.config přidejte do projektu.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a>Vytvoření klientské aplikace  
  
1.  Přidat nový projekt konzolové aplikace s názvem `Client` do řešení. Přidejte odkaz na System.Activities.dll.  
  
2.  Otevřete soubor program.cs a přidejte následující kód.  
  
    ```  
    class Program  
        {  
  
            private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
            static void Main(string[] args)  
            {  
                //Build client  
                Console.WriteLine("Building the client.");  
                WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
                client.Completed = Program.Completed;  
                client.Aborted = Program.Aborted;  
                client.OnUnhandledException = Program.OnUnhandledException;  
  
                //Wait for service to start  
                Console.WriteLine("Press ENTER once service is started.");  
                Console.ReadLine();  
  
                //Start the client              
                Console.WriteLine("Starting the client.");  
                client.Run();  
                syncEvent.WaitOne();  
  
                //Sample complete  
                Console.WriteLine();  
                Console.WriteLine("Client complete. Press ENTER to exit.");  
                Console.ReadLine();  
            }  
  
            private static void Completed(WorkflowApplicationCompletedEventArgs e)  
            {  
                Program.syncEvent.Set();  
            }  
  
            private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
            {  
                Console.WriteLine("Client Aborted: {0}", e.Reason);  
                Program.syncEvent.Set();  
            }  
  
            private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
            {  
                Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
                return UnhandledExceptionAction.Cancel;  
            }  
        }  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Přehled transakcí ve Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
