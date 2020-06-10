---
title: Tok transakcí do služeb pracovních postupů a mimo ně
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 17c05139b5977c47e20e888e436a311ba145018a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597459"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Tok transakcí do služeb pracovních postupů a mimo ně
Služby pracovních postupů a klienti se můžou zúčastnit transakcí.  Aby se operace služby stala součástí okolí transakce, umístěte <xref:System.ServiceModel.Activities.Receive> aktivitu do <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. Všechna volání prováděná <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> aktivitou nebo v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> budou také vytvořena v rámci okolí transakce. Klientská aplikace pracovního postupu může vytvořit okolí transakce pomocí <xref:System.Activities.Statements.TransactionScope> aktivity služby a volat operace služeb pomocí ambientní transakce. Toto téma vás provede vytvořením služby pracovního postupu a klienta pracovního postupu, který se účastní transakcí.  
  
> [!WARNING]
> Pokud je instance služby pracovního postupu načtená v rámci transakce a pracovní postup obsahuje <xref:System.Activities.Statements.Persist> aktivitu, instance pracovního postupu se zablokuje, dokud nevyprší časový limit transakce.  
  
> [!IMPORTANT]
> Pokaždé, když použijete pracovní <xref:System.ServiceModel.Activities.TransactedReceiveScope> postup, se doporučuje umístit všechny přijaté aktivity do pracovního postupu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivit.  
  
> [!IMPORTANT]
> Při použití <xref:System.ServiceModel.Activities.TransactedReceiveScope> a doručení zpráv v nesprávném pořadí bude pracovní postup při pokusu o doručení první zprávy mimo pořadí přerušen. Je nutné zajistit, aby byl pracovní postup vždy v konzistentním bodu zastavení v případě nečinnosti pracovního postupu. To vám umožní restartovat pracovní postup z předchozího bodu trvalosti, aby se pracovní postup přerušil.  
  
### <a name="create-a-shared-library"></a>Vytvoření sdílené knihovny  
  
1. Vytvořte nové prázdné řešení sady Visual Studio.  
  
2. Přidejte nový projekt knihovny tříd s názvem `Common` . Přidejte odkazy na následující sestavení:  
  
    - System. Activities. dll  
  
    - System.ServiceModel.dll  
  
    - System. ServiceModel. Activities. dll  
  
    - System.Transactions.dll  
  
3. Přidejte do projektu novou třídu s názvem `PrintTransactionInfo` `Common` . Tato třída je odvozena z <xref:System.Activities.NativeActivity> a přetížení <xref:System.Activities.NativeActivity.Execute%2A> metody.  
  
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
  
1. Přidejte do projektu novou službu pracovního postupu WCF volanou `WorkflowService` `Common` . Provedete to tak, že kliknete pravým tlačítkem na `Common` projekt, vyberte **Přidat**, **Nová položka...**, vyberte **pracovní postup** v části **Nainstalované šablony** a vyberte **Služba pracovního postupu WCF**.  
  
     ![Přidání služby pracovního postupu](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Odstraňte výchozí `ReceiveRequest` aktivity a `SendResponse` .  
  
3. Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu do `Sequential Service` aktivity. Nastavte vlastnost text na `"Workflow Service starting ..."` , jak je znázorněno v následujícím příkladu.  
  
     ! [Přidání aktivity WriteLine do aktivity sekvenční služby (./Media/Flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)  
  
4. Přetáhněte <xref:System.ServiceModel.Activities.TransactedReceiveScope> za <xref:System.Activities.Statements.WriteLine> aktivitu. <xref:System.ServiceModel.Activities.TransactedReceiveScope>Aktivitu najdete v části pro **zasílání zpráv** v **sadě nástrojů**. <xref:System.ServiceModel.Activities.TransactedReceiveScope>Aktivita se skládá ze dvou částí **žádosti** a **textu**. Část **žádosti** obsahuje <xref:System.ServiceModel.Activities.Receive> aktivitu. Oddíl **text** obsahuje aktivity, které se mají provést v rámci transakce po přijetí zprávy.  
  
     ![Přidání aktivity TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Vyberte <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivitu a klikněte na tlačítko **proměnné** . Přidejte následující proměnné.  
  
     ![Přidávání proměnných do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Můžete odstranit datovou proměnnou, která je ve výchozím nastavení. Můžete také použít existující proměnnou popisovače.  
  
6. Přetáhněte <xref:System.ServiceModel.Activities.Receive> aktivitu v části **žádosti** <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. Nastavte následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |CanCreateInstance|Pravda (zaškrtněte políčko)|  
    |OperationName|StartSample|  
    |Stejnými ServiceContractName|ITransactionSample|  
  
     Pracovní postup by měl vypadat takto:  
  
     ![Přidání aktivity Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. V aktivitě klikněte na odkaz **definovat...** <xref:System.ServiceModel.Activities.Receive> a proveďte následující nastavení:  
  
     ![Nastavení nastavení zpráv pro aktivitu Receive](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Přetáhněte <xref:System.Activities.Statements.Sequence> aktivitu do části text v <xref:System.ServiceModel.Activities.TransactedReceiveScope> . V rámci <xref:System.Activities.Statements.Sequence> aktivity přetahujte a přetáhněte dvě <xref:System.Activities.Statements.WriteLine> aktivity a nastavte <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnosti, jak je znázorněno v následující tabulce.  
  
    |Aktivita|Hodnota|  
    |--------------|-----------|  
    |1. WriteLine|"Služba: přijímání dokončeno"|  
    |druhý WriteLine|"Service: Received =" + requestMessage|  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Sekvence po přidání aktivit WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Přetáhněte `PrintTransactionInfo` aktivitu za druhou <xref:System.Activities.Statements.WriteLine> aktivitu v **těle** <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.  
  
     ![Sekvence po přidání PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Přetáhněte <xref:System.Activities.Statements.Assign> aktivitu za `PrintTransactionInfo` aktivitu a nastavte její vlastnosti podle následující tabulky.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |Akce|replyMessage|  
    |Hodnota|"Služba: odesílá se odpověď."|  
  
11. Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu za <xref:System.Activities.Statements.Assign> aktivitou a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "služba: zahájit odpověď".  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Po přidání přiřadit a odwriteline](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Klikněte pravým tlačítkem na <xref:System.ServiceModel.Activities.Receive> aktivitu a vyberte **vytvořit aktivitu SendReply** a vložte ji za poslední <xref:System.Activities.Statements.WriteLine> aktivitu. V aktivitě klikněte na odkaz **definovat...** `SendReplyToReceive` a proveďte následující nastavení.  
  
     ![Nastavení zprávy s odpovědí](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu za `SendReplyToReceive` aktivitou a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "služba: odpověď poslána".  
  
14. Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu do dolní části pracovního postupu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "služba: pracovní postup končí, stiskněte klávesu ENTER pro ukončení."  
  
     Dokončený pracovní postup služby by měl vypadat takto:  
  
     ![Dokončení pracovního postupu služby](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Implementace klienta pracovního postupu  
  
1. Přidejte novou aplikaci pracovního postupu WCF, která se volá `WorkflowClient` do `Common` projektu. Chcete-li to provést, klikněte pravým tlačítkem myši na `Common` projekt, vyberte možnost **Přidat**, **Nová položka...**, vyberte možnost **pracovní postup** v části **Nainstalované šablony** a vyberte **aktivita**.  
  
     ![Přidat projekt aktivity](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Přetáhněte <xref:System.Activities.Statements.Sequence> aktivitu na návrhovou plochu.  
  
3. V rámci <xref:System.Activities.Statements.Sequence> aktivity přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na `"Client: Workflow starting"` . Pracovní postup by teď měl vypadat takto:  
  
     ![Přidání aktivity WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Přetáhněte <xref:System.Activities.Statements.TransactionScope> aktivitu za <xref:System.Activities.Statements.WriteLine> aktivitou.  Vyberte <xref:System.Activities.Statements.TransactionScope> aktivitu, klikněte na tlačítko proměnné a přidejte následující proměnné.  
  
     ![Přidat proměnné do objektu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Přetáhněte <xref:System.Activities.Statements.Sequence> aktivitu do těla <xref:System.Activities.Statements.TransactionScope> aktivity.  
  
6. Přetáhněte `PrintTransactionInfo` aktivitu v rámci<xref:System.Activities.Statements.Sequence>  
  
7. Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu za `PrintTransactionInfo` aktivitu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "klient: začátek odeslání". Pracovní postup by teď měl vypadat takto:  
  
     ![Přidávání klienta: zahájení aktivit odeslání](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Přetáhněte <xref:System.ServiceModel.Activities.Send> aktivitu za <xref:System.Activities.Statements.Assign> aktivitu a nastavte následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |Stejnými ServiceContractName|ITransactionSample|  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Nastavení vlastností aktivity odeslání](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Klikněte na odkaz **definovat...** a proveďte následující nastavení:  
  
     ![Odeslat nastavení zprávy o aktivitě](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Klikněte pravým tlačítkem na <xref:System.ServiceModel.Activities.Send> aktivitu a vyberte **vytvořit ReceiveReply**. <xref:System.ServiceModel.Activities.ReceiveReply>Aktivita se automaticky umístí za <xref:System.ServiceModel.Activities.Send> aktivitu.  
  
11. Klikněte na definovat... Propojte aktivitu ReceiveReplyForSend a proveďte následující nastavení:  
  
     ![Nastavení zprávy ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu mezi <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> aktivitami a a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "klient: Odeslat dokončeno".  
  
13. Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu za <xref:System.ServiceModel.Activities.ReceiveReply> aktivitu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na stranu klienta: odpověď přijata = "+ replyMessage  
  
14. Přetáhněte `PrintTransactionInfo` aktivitu za <xref:System.Activities.Statements.WriteLine> aktivitou.  
  
15. Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu na konci pracovního postupu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "pracovní postup klienta končí." Dokončený pracovní postup klienta by měl vypadat jako v následujícím diagramu.  
  
     ![Dokončený pracovní postup klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Sestavte řešení.  
  
### <a name="create-the-service-application"></a>Vytvoření aplikace služby  
  
1. Přidejte do řešení nový projekt konzolové aplikace s názvem `Service` . Přidejte odkazy na následující sestavení:  
  
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
  
1. Přidejte do řešení nový projekt konzolové aplikace s názvem `Client` . Přidejte odkaz na System. Activities. dll.  
  
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

- [Služby pracovních postupů](workflow-services.md)
- [Transakce ve Windows Communication Foundation – přehled](transactions-overview.md)
