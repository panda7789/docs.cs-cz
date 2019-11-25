---
title: Tok transakcí do služeb pracovních postupů a mimo ně
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: ea14bc651258684fd31940aa6b88f9731348dcd1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978272"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Tok transakcí do služeb pracovních postupů a mimo ně
Služby pracovních postupů a klienti se můžou zúčastnit transakcí.  Aby se operace služby stala součástí okolí transakce, umístěte <xref:System.ServiceModel.Activities.Receive>ovou aktivitu do aktivity <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Všechna volání prováděná <xref:System.ServiceModel.Activities.Send> nebo aktivitou <xref:System.ServiceModel.Activities.SendReply> v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> budou také vytvořena v rámci okolí transakce. Klientská aplikace pracovního postupu může vytvořit ambientní transakci pomocí <xref:System.Activities.Statements.TransactionScope> aktivity a volat operace služeb pomocí ambientní transakce. Toto téma vás provede vytvořením služby pracovního postupu a klienta pracovního postupu, který se účastní transakcí.  
  
> [!WARNING]
> Pokud je instance služby pracovního postupu načtená v rámci transakce a pracovní postup obsahuje aktivitu <xref:System.Activities.Statements.Persist>, instance pracovního postupu se zablokuje, dokud nevyprší časový limit transakce.  
  
> [!IMPORTANT]
> Pokaždé, když použijete <xref:System.ServiceModel.Activities.TransactedReceiveScope>, doporučuje se umístit všechny přijaté pracovní postupy v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivit.  
  
> [!IMPORTANT]
> Při použití <xref:System.ServiceModel.Activities.TransactedReceiveScope> a zpráv v nesprávném pořadí bude pracovní postup při pokusu o doručení první zprávy mimo pořadí přerušen. Je nutné zajistit, aby byl pracovní postup vždy v konzistentním bodu zastavení v případě nečinnosti pracovního postupu. To vám umožní restartovat pracovní postup z předchozího bodu trvalosti, aby se pracovní postup přerušil.  
  
### <a name="create-a-shared-library"></a>Vytvoření sdílené knihovny  
  
1. Vytvořte nové prázdné řešení sady Visual Studio.  
  
2. Přidejte nový projekt knihovny tříd s názvem `Common`. Přidejte odkazy na následující sestavení:  
  
    - System. Activities. dll  
  
    - System.ServiceModel.dll  
  
    - System. ServiceModel. Activities. dll  
  
    - System.Transactions.dll  
  
3. Do projektu `Common` přidejte novou třídu s názvem `PrintTransactionInfo`. Tato třída je odvozena z <xref:System.Activities.NativeActivity> a přetížení metody <xref:System.Activities.NativeActivity.Execute%2A>.  
  
    ```csharp
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
  
     Toto je nativní aktivita, která zobrazuje informace o okolí transakce a používá se v pracovních postupech služby i klienta, které jsou používány v tomto tématu. Sestavte řešení, aby tato aktivita byla k dispozici v části **společná** v **sadě nástrojů**.  
  
### <a name="implement-the-workflow-service"></a>Implementace služby pracovního postupu  
  
1. Přidejte do projektu `Common` novou službu pracovního postupu WCF nazvanou `WorkflowService`. To uděláte tak, že kliknete pravým tlačítkem na projekt `Common`, vyberte **Přidat**, **Nová položka...** , vyberte **pracovní postup** v části **Nainstalované šablony** a vyberte **Služba pracovního postupu WCF**.  
  
     ![Přidání služby pracovního postupu](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Odstraní výchozí `ReceiveRequest` a `SendResponse` aktivity.  
  
3. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> do aktivity `Sequential Service`. Nastavte vlastnost text na `"Workflow Service starting ..."`, jak je znázorněno v následujícím příkladu.  
  
     ! [Přidání aktivity WriteLine do aktivity sekvenční služby (./Media/Flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)  
  
4. Přetáhněte <xref:System.ServiceModel.Activities.TransactedReceiveScope> za aktivitu <xref:System.Activities.Statements.WriteLine>. Aktivitu <xref:System.ServiceModel.Activities.TransactedReceiveScope> lze nalézt v části pro **zasílání zpráv** v **sadě nástrojů**. Aktivita <xref:System.ServiceModel.Activities.TransactedReceiveScope> se skládá ze dvou částí **žádosti** a **textu**. Oddíl **Request** obsahuje aktivitu <xref:System.ServiceModel.Activities.Receive>. Oddíl **text** obsahuje aktivity, které se mají provést v rámci transakce po přijetí zprávy.  
  
     ![Přidání aktivity TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Vyberte aktivitu <xref:System.ServiceModel.Activities.TransactedReceiveScope> a klikněte na tlačítko **proměnné** . Přidejte následující proměnné.  
  
     ![Přidávání proměnných do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Můžete odstranit datovou proměnnou, která je ve výchozím nastavení. Můžete také použít existující proměnnou popisovače.  
  
6. Přetáhněte aktivitu <xref:System.ServiceModel.Activities.Receive> v části **žádosti** aktivity <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Nastavte následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |CanCreateInstance|Pravda (zaškrtněte políčko)|  
    |OperationName|StartSample|  
    |Stejnými ServiceContractName|ITransactionSample|  
  
     Pracovní postup by měl vypadat takto:  
  
     ![Přidání aktivity Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. Klikněte na odkaz **definovat...** v aktivitě <xref:System.ServiceModel.Activities.Receive> a proveďte následující nastavení:  
  
     ![Nastavení nastavení zpráv pro aktivitu Receive](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Přetáhněte aktivitu <xref:System.Activities.Statements.Sequence> do části <xref:System.ServiceModel.Activities.TransactedReceiveScope>tělo. V rámci aktivity <xref:System.Activities.Statements.Sequence> přetáhněte dvě aktivity <xref:System.Activities.Statements.WriteLine> a nastavte vlastnosti <xref:System.Activities.Statements.WriteLine.Text%2A>, jak je znázorněno v následující tabulce.  
  
    |Aktivita|Hodnota|  
    |--------------|-----------|  
    |1\. WriteLine|"Služba: přijímání dokončeno"|  
    |druhý WriteLine|"Service: Received =" + requestMessage|  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Sekvence po přidání aktivit WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Přetáhněte aktivitu `PrintTransactionInfo` za druhou aktivitu <xref:System.Activities.Statements.WriteLine> v **těle** aktivity <xref:System.ServiceModel.Activities.TransactedReceiveScope>.  
  
     ![Sekvence po přidání PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Přetáhněte aktivitu <xref:System.Activities.Statements.Assign> po aktivitě `PrintTransactionInfo` a nastavte její vlastnosti podle následující tabulky.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |Chcete-li|replyMessage|  
    |Hodnota|"Služba: odesílá se odpověď."|  
  
11. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> po aktivitě <xref:System.Activities.Statements.Assign> a nastavte její vlastnost <xref:System.Activities.Statements.WriteLine.Text%2A> na "služba: zahájit odpověď".  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Po přidání přiřadit a odwriteline](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Klikněte pravým tlačítkem myši na aktivitu <xref:System.ServiceModel.Activities.Receive> a vyberte **vytvořit aktivitu SendReply** a vložte ji za poslední aktivitu <xref:System.Activities.Statements.WriteLine>. V aktivitě `SendReplyToReceive` klikněte na odkaz **definovat...** a proveďte následující nastavení.  
  
     ![Nastavení zprávy s odpovědí](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> po aktivitě `SendReplyToReceive` a nastavte ji jako vlastnost <xref:System.Activities.Statements.WriteLine.Text%2A> na služba: odpověď odeslána.  
  
14. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> v dolní části pracovního postupu a nastavte její vlastnost <xref:System.Activities.Statements.WriteLine.Text%2A> na "služba: pracovní postup končí, stiskněte klávesu ENTER pro ukončení."  
  
     Dokončený pracovní postup služby by měl vypadat takto:  
  
     ![Dokončení pracovního postupu služby](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Implementace klienta pracovního postupu  
  
1. Přidejte novou aplikaci pracovního postupu WCF nazvanou `WorkflowClient` do projektu `Common`. To uděláte tak, že kliknete pravým tlačítkem na projekt `Common`, vyberte **Přidat**, **Nová položka...** , vyberte **pracovní postup** v části **Nainstalované šablony** a vyberte **aktivita**.  
  
     ![Přidat projekt aktivity](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Přetáhněte aktivitu <xref:System.Activities.Statements.Sequence> na návrhovou plochu.  
  
3. V rámci aktivity <xref:System.Activities.Statements.Sequence> přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> a nastavte její vlastnost <xref:System.Activities.Statements.WriteLine.Text%2A> na `"Client: Workflow starting"`. Pracovní postup by teď měl vypadat takto:  
  
     ![Přidání aktivity WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Přetáhněte aktivitu <xref:System.Activities.Statements.TransactionScope> po aktivitě <xref:System.Activities.Statements.WriteLine>.  Vyberte aktivitu <xref:System.Activities.Statements.TransactionScope>, klikněte na tlačítko proměnné a přidejte následující proměnné.  
  
     ![Přidat proměnné do objektu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Přetáhněte aktivitu <xref:System.Activities.Statements.Sequence> do těla aktivity <xref:System.Activities.Statements.TransactionScope>.  
  
6. Přetažení `PrintTransactionInfo` aktivity v rámci <xref:System.Activities.Statements.Sequence>  
  
7. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> po aktivitě `PrintTransactionInfo` a nastavte její vlastnost <xref:System.Activities.Statements.WriteLine.Text%2A> na "klient: začátek odeslání". Pracovní postup by teď měl vypadat takto:  
  
     ![Přidávání klienta: zahájení aktivit odeslání](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Přetáhněte aktivitu <xref:System.ServiceModel.Activities.Send> po aktivitě <xref:System.Activities.Statements.Assign> a nastavte následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |Stejnými ServiceContractName|ITransactionSample|  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Nastavení vlastností aktivity odeslání](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Klikněte na odkaz **definovat...** a proveďte následující nastavení:  
  
     ![Odeslat nastavení zprávy o aktivitě](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Klikněte pravým tlačítkem myši na aktivitu <xref:System.ServiceModel.Activities.Send> a vyberte **vytvořit ReceiveReply**. Aktivita <xref:System.ServiceModel.Activities.ReceiveReply> bude automaticky umístěna po aktivitě <xref:System.ServiceModel.Activities.Send>.  
  
11. Klikněte na definovat... Propojte aktivitu ReceiveReplyForSend a proveďte následující nastavení:  
  
     ![Nastavení zprávy ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> mezi <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity a nastavte její vlastnost <xref:System.Activities.Statements.WriteLine.Text%2A> na "klient: Odeslat dokončeno".  
  
13. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> po aktivitě <xref:System.ServiceModel.Activities.ReceiveReply> a nastavte její vlastnost <xref:System.Activities.Statements.WriteLine.Text%2A> na stranu klienta: odpověď přijata = "+ replyMessage  
  
14. Přetáhněte aktivitu `PrintTransactionInfo` po aktivitě <xref:System.Activities.Statements.WriteLine>.  
  
15. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> na konci pracovního postupu a nastavte její vlastnost <xref:System.Activities.Statements.WriteLine.Text%2A> na "pracovní postup klienta končí." Dokončený pracovní postup klienta by měl vypadat jako v následujícím diagramu.  
  
     ![Dokončený pracovní postup klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Sestavte řešení.  
  
### <a name="create-the-service-application"></a>Vytvoření aplikace služby  
  
1. Přidejte do řešení nový projekt konzolové aplikace s názvem `Service`. Přidejte odkazy na následující sestavení:  
  
    1. System. Activities. dll  
  
    2. System.ServiceModel.dll  
  
    3. System. ServiceModel. Activities. dll  
  
2. Otevřete vygenerovaný soubor Program.cs a následující kód:  
  
    ```csharp
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
  
3. Do projektu přidejte následující soubor App. config.  
  
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
  
1. Přidejte do řešení nový projekt konzolové aplikace s názvem `Client`. Přidejte odkaz na System. Activities. dll.  
  
2. Otevřete soubor program.cs a přidejte následující kód.  
  
    ```csharp
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
