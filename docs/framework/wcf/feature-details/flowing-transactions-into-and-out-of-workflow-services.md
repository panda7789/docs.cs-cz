---
title: Tok transakcí do služeb pracovních postupů a mimo ně
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: fe03047dd931d25ec94bbc5e00c479d1b42397bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185269"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Tok transakcí do služeb pracovních postupů a mimo ně
Služby pracovního postupu a klienti se mohou účastnit transakcí.  Chcete-li, aby se operace služby <xref:System.ServiceModel.Activities.Receive> stala součástí <xref:System.ServiceModel.Activities.TransactedReceiveScope> transakce okolí, umístěte aktivitu v rámci aktivity. Jakékoli hovory provedené <xref:System.ServiceModel.Activities.Send> nebo <xref:System.ServiceModel.Activities.SendReply> aktivity <xref:System.ServiceModel.Activities.TransactedReceiveScope> v rámci bude také v rámci okolí transakce. Klientská aplikace pracovního postupu můžete <xref:System.Activities.Statements.TransactionScope> vytvořit okolní transakce pomocí operace aktivity a volání služby pomocí okolí transakce. Toto téma vás provede vytvořením služby pracovního postupu a klienta pracovního postupu, kteří se účastní transakcí.  
  
> [!WARNING]
> Pokud je instance služby pracovního postupu načtena v rámci transakce a pracovní postup obsahuje aktivitu, <xref:System.Activities.Statements.Persist> instance pracovního postupu se zablokuje, dokud neskončí časový výplní transakce.  
  
> [!IMPORTANT]
> Vždy, když <xref:System.ServiceModel.Activities.TransactedReceiveScope> používáte se doporučuje umístit všechny <xref:System.ServiceModel.Activities.TransactedReceiveScope> Příjem v pracovním postupu v rámci aktivit.  
  
> [!IMPORTANT]
> Při <xref:System.ServiceModel.Activities.TransactedReceiveScope> použití a zprávy dorazí v nesprávném pořadí, pracovní postup bude přerušena při pokusu o doručení první zprávy mimo pořadí. Je nutné zajistit, aby byl pracovní postup vždy v konzistentním bodě zastavení při nečinnosti pracovního postupu. To vám umožní restartovat pracovní postup z předchozího bodu trvalosti, pokud by byl pracovní postup přerušen.  
  
### <a name="create-a-shared-library"></a>Vytvoření sdílené knihovny  
  
1. Vytvořte nové prázdné řešení sady Visual Studio.  
  
2. Přidejte nový projekt `Common`knihovny tříd s názvem . Přidejte odkazy na následující sestavení:  
  
    - Soubor System.Activities.dll  
  
    - System.ServiceModel.dll  
  
    - Soubor System.ServiceModel.Activities.dll  
  
    - System.Transactions.dll  
  
3. Přidejte novou `PrintTransactionInfo` třídu `Common` volanou do projektu. Tato třída je <xref:System.Activities.NativeActivity> odvozen a <xref:System.Activities.NativeActivity.Execute%2A> přetížení metody.  
  
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
  
     Toto je nativní aktivita, která zobrazuje informace o okolí transakce a používá se v pracovních postupech služby i klienta použitých v tomto tématu. Vytvořte řešení, které tuto aktivitu zpřístupní v **části Společné** v **panelu nástrojů**.  
  
### <a name="implement-the-workflow-service"></a>Implementace služby pracovního postupu  
  
1. Přidejte novou službu pracovního postupu WCF, která je volána `WorkflowService` do `Common` projektu. Chcete-li to `Common` provést pravým tlačítkem myši na projekt, vyberte **přidat**, **nová položka ...**, vybrat pracovní **postup** v části **Nainstalované šablony** a vyberte **službu pracovního postupu WCF**.  
  
     ![Přidání služby pracovního postupu](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Odstraňte `ReceiveRequest` výchozí `SendResponse` nastavení a aktivity.  
  
3. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> do `Sequential Service` aktivity. Nastavte vlastnost text `"Workflow Service starting ..."` tak, jak je znázorněno v následujícím příkladu.  
  
     ! [Přidání aktivity WriteLine do aktivity sekvenční služby(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)  
  
4. Za aktivitou <xref:System.ServiceModel.Activities.TransactedReceiveScope> <xref:System.Activities.Statements.WriteLine> přetáhněte a. Aktivitu <xref:System.ServiceModel.Activities.TransactedReceiveScope> naleznete v části **Zasílání zpráv** v **panelu nástrojů**. Aktivita <xref:System.ServiceModel.Activities.TransactedReceiveScope> se skládá ze dvou částí **Request** a **Body**. Část **Požadavek** <xref:System.ServiceModel.Activities.Receive> obsahuje aktivitu. Část **Body** obsahuje aktivity, které mají být provedeny v rámci transakce po přijetí zprávy.  
  
     ![Přidání aktivity TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Vyberte <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivitu a klepněte na tlačítko **Proměnné.** Přidejte následující proměnné.  
  
     ![Přidání proměnných do transactedreceivescope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Můžete odstranit datovou proměnnou, která je k dispozici ve výchozím nastavení. Můžete také použít existující proměnnou popisovače.  
  
6. Přetáhněte aktivitu <xref:System.ServiceModel.Activities.Receive> v části **Požadavek** aktivity. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Nastavte následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |Cancreateinstance|True (zaškrtněte políčko)|  
    |OperationName|StartSample|  
    |Název_kontraktu_service_kontraktu|ITransactionSample|  
  
     Pracovní postup by měl vypadat takto:  
  
     ![Přidání aktivity příjmu](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. Klikněte na odkaz <xref:System.ServiceModel.Activities.Receive> **Definovat...** v aktivitě a proveďte následující nastavení:  
  
     ![Nastavení nastavení zprávy pro aktivitu příjmu](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Přetáhněte aktivitu <xref:System.Activities.Statements.Sequence> do části Tělo <xref:System.ServiceModel.Activities.TransactedReceiveScope>v . V <xref:System.Activities.Statements.Sequence> rámci aktivity <xref:System.Activities.Statements.WriteLine> přetáhněte dvě <xref:System.Activities.Statements.WriteLine.Text%2A> aktivity a nastavte vlastnosti, jak je znázorněno v následující tabulce.  
  
    |Aktivita|Hodnota|  
    |--------------|-----------|  
    |1. WriteLine|"Služba: Příjem dokončen"|  
    |2. WriteLine|"Služba: Přijato = " + requestMessage|  
  
     Pracovní postup by nyní měl vypadat takto:  
  
     ![Posloupnost po přidání aktivit WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. `PrintTransactionInfo` Přetáhněte aktivitu po <xref:System.Activities.Statements.WriteLine> druhé aktivitě v <xref:System.ServiceModel.Activities.TransactedReceiveScope> **těle** v aktivitě.  
  
     ![Sekvence po přidání PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Přetáhněte aktivitu <xref:System.Activities.Statements.Assign> za `PrintTransactionInfo` aktivitou a nastavte její vlastnosti podle následující tabulky.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |Akce|replyMessage|  
    |Hodnota|"Služba: Odeslání odpovědi."|  
  
11. Po aktivitě <xref:System.Activities.Statements.WriteLine> přetáhněte <xref:System.Activities.Statements.Assign> aktivitu <xref:System.Activities.Statements.WriteLine.Text%2A> a nastavte její vlastnost na "Služba: Zahájit odpověď".  
  
     Pracovní postup by nyní měl vypadat takto:  
  
     ![Po přidání přiřadit a writeline](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Klikněte <xref:System.ServiceModel.Activities.Receive> pravým tlačítkem myši na aktivitu <xref:System.Activities.Statements.WriteLine> a vyberte **Vytvořit odeslanou odpověď** a vložte ji po poslední aktivitě. Klikněte na odkaz `SendReplyToReceive` **Definovat...** v aktivitě a proveďte následující nastavení.  
  
     ![Nastavení odpovědi na zprávu](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Po aktivitě <xref:System.Activities.Statements.WriteLine> přetáhněte `SendReplyToReceive` aktivitu a <xref:System.Activities.Statements.WriteLine.Text%2A> nastavte její vlastnost na "Služba: Odeslaná odpověď".  
  
14. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> v dolní části pracovního <xref:System.Activities.Statements.WriteLine.Text%2A> postupu a nastavte její vlastnost na "Služba: Ukončení pracovního postupu, ukončení stisknutím klávesy ENTER".  
  
     Pracovní postup dokončené služby by měl vypadat takto:  
  
     ![Dokončení pracovního postupu služby](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Implementace klienta pracovního postupu  
  
1. Přidejte novou aplikaci wcf workflow, volána `WorkflowClient` do `Common` projektu. Chcete-li to `Common` provést pravým tlačítkem myši na projekt, vyberte **přidat**, **nová položka ...**, vybrat pracovní **postup** v části **Nainstalované šablony** a vyberte **aktivita**.  
  
     ![Přidání projektu aktivity](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Přetáhněte aktivitu <xref:System.Activities.Statements.Sequence> na plochu návrhu.  
  
3. V <xref:System.Activities.Statements.Sequence> rámci aktivity <xref:System.Activities.Statements.WriteLine> přetáhněte aktivitu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na `"Client: Workflow starting"`. Pracovní postup by nyní měl vypadat takto:  
  
     ![Přidání aktivity WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Po aktivitě <xref:System.Activities.Statements.TransactionScope> přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu.  Vyberte <xref:System.Activities.Statements.TransactionScope> aktivitu, klepněte na tlačítko Proměnné a přidejte následující proměnné.  
  
     ![Přidání proměnných do oboru transakce](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Přetáhněte aktivitu <xref:System.Activities.Statements.Sequence> do těla <xref:System.Activities.Statements.TransactionScope> aktivity.  
  
6. Přetáhněte aktivitu `PrintTransactionInfo` v rámci<xref:System.Activities.Statements.Sequence>  
  
7. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> za `PrintTransactionInfo` aktivitou <xref:System.Activities.Statements.WriteLine.Text%2A> a nastavte její vlastnost na "Klient: Počáteční odeslání". Pracovní postup by nyní měl vypadat takto:  
  
     ![Přidání klienta: Zahájení odesílání aktivit](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Přetáhněte aktivitu <xref:System.ServiceModel.Activities.Send> za <xref:System.Activities.Statements.Assign> aktivitou a nastavte následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |Název konfigurace koncového bodu|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |Název_kontraktu_service_kontraktu|ITransactionSample|  
  
     Pracovní postup by nyní měl vypadat takto:  
  
     ![Nastavení vlastností aktivity Odeslat](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Klikněte na odkaz **Definovat...** a proveďte následující nastavení:  
  
     ![Odeslat nastavení zprávy o aktivitě](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Klepněte <xref:System.ServiceModel.Activities.Send> pravým tlačítkem myši na aktivitu a vyberte **příkaz Vytvořit receivereply**. Aktivita <xref:System.ServiceModel.Activities.ReceiveReply> bude automaticky umístěna po aktivitě. <xref:System.ServiceModel.Activities.Send>  
  
11. Klikněte na definovat... na aktivitu ReceiveReplyForSend a proveďte následující nastavení:  
  
     ![Nastavení zprávy ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <xref:System.Activities.Statements.WriteLine> Přetáhněte aktivitu mezi <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> aktivitami <xref:System.Activities.Statements.WriteLine.Text%2A> a nastavte její vlastnost na "Klient: Odeslat dokončeno".  
  
13. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> po <xref:System.ServiceModel.Activities.ReceiveReply> aktivitě <xref:System.Activities.Statements.WriteLine.Text%2A> a nastavte její vlastnost na "Strana klienta: Odpověď přijata = " + replyMessage  
  
14. Po aktivitě `PrintTransactionInfo` přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu.  
  
15. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> na konci pracovního postupu <xref:System.Activities.Statements.WriteLine.Text%2A> a nastavte její vlastnost na "Ukončení pracovního postupu klienta". Dokončený pracovní postup klienta by měl vypadat jako následující diagram.  
  
     ![Dokončený pracovní postup klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Sestavte řešení.  
  
### <a name="create-the-service-application"></a>Vytvořit aplikaci Service  
  
1. Přidejte do řešení `Service` nový projekt konzolové aplikace svolaný do řešení. Přidejte odkazy na následující sestavení:  
  
    1. Soubor System.Activities.dll  
  
    2. System.ServiceModel.dll  
  
    3. Soubor System.ServiceModel.Activities.dll  
  
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
  
3. Přidejte do projektu následující soubor app.config.  
  
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
  
1. Přidejte do řešení `Client` nový projekt konzolové aplikace svolaný do řešení. Přidejte odkaz na soubor System.Activities.dll.  
  
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
  
## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Transakce ve Windows Communication Foundation – přehled](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
