---
title: Tok transakcí do služeb pracovních postupů a mimo ně
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: ae99c53bbb859f3ade075d4d60ad2ae7e5e7272b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988810"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Tok transakcí do služeb pracovních postupů a mimo ně
Služby pracovních postupů a klienti se můžou zúčastnit transakcí.  Aby se operace služby stala součástí okolí transakce, umístěte <xref:System.ServiceModel.Activities.Receive> aktivitu <xref:System.ServiceModel.Activities.TransactedReceiveScope> do aktivity. Všechna volání prováděná <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> aktivitou nebo v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> budou také vytvořena v rámci okolí transakce. Klientská aplikace pracovního postupu může vytvořit okolí transakce <xref:System.Activities.Statements.TransactionScope> pomocí aktivity služby a volat operace služeb pomocí ambientní transakce. Toto téma vás provede vytvořením služby pracovního postupu a klienta pracovního postupu, který se účastní transakcí.  
  
> [!WARNING]
> Pokud je instance služby pracovního postupu načtená v rámci transakce a pracovní postup obsahuje <xref:System.Activities.Statements.Persist> aktivitu, instance pracovního postupu se zablokuje, dokud nevyprší časový limit transakce.  
  
> [!IMPORTANT]
> Pokaždé, když <xref:System.ServiceModel.Activities.TransactedReceiveScope> použijete pracovní postup, se doporučuje umístit všechny přijaté aktivity <xref:System.ServiceModel.Activities.TransactedReceiveScope> do pracovního postupu v rámci aktivit.  
  
> [!IMPORTANT]
> Při použití <xref:System.ServiceModel.Activities.TransactedReceiveScope> a doručení zpráv v nesprávném pořadí bude pracovní postup při pokusu o doručení první zprávy mimo pořadí přerušen. Je nutné zajistit, aby byl pracovní postup vždy v konzistentním bodu zastavení v případě nečinnosti pracovního postupu. To vám umožní restartovat pracovní postup z předchozího bodu trvalosti, aby se pracovní postup přerušil.  
  
### <a name="create-a-shared-library"></a>Vytvoření sdílené knihovny  
  
1. Vytvořte nové prázdné řešení sady Visual Studio.  
  
2. Přidejte nový projekt knihovny tříd s názvem `Common`. Přidejte odkazy na následující sestavení:  
  
    - System.Activities.dll  
  
    - System.ServiceModel.dll  
  
    - System.ServiceModel.Activities.dll  
  
    - System.Transactions.dll  
  
3. `PrintTransactionInfo` Přidejte`Common` do projektu novou třídu s názvem. Tato třída je odvozena <xref:System.Activities.NativeActivity> z a přetížení <xref:System.Activities.NativeActivity.Execute%2A> metody.  
  
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
  
     Toto je nativní aktivita, která zobrazuje informace o okolí transakce a používá se v pracovních postupech služby i klienta, které jsou používány v tomto tématu. Sestavte řešení, aby tato aktivita byla k dispozici v části **společná** v **sadě nástrojů**.  
  
### <a name="implement-the-workflow-service"></a>Implementace služby pracovního postupu  
  
1. `WorkflowService` Přidejte`Common` do projektu novou službu pracovního postupu WCF volanou. Provedete to tak, `Common` že kliknete pravým tlačítkem na projekt, vyberte **Přidat**, **Nová položka...** , vyberte **pracovní postup** v části **Nainstalované šablony** a vyberte **Služba pracovního postupu WCF**.  
  
     ![Přidání služby pracovního postupu](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Odstraňte výchozí `ReceiveRequest` aktivity a `SendResponse` .  
  
3. <xref:System.Activities.Statements.WriteLine> Přetáhněte aktivitu`Sequential Service` do aktivity. Nastavte vlastnost text na `"Workflow Service starting ..."` , jak je znázorněno v následujícím příkladu.  
  
     ! [Přidání aktivity WriteLine do aktivity sekvenční služby (./Media/Flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)  
  
4. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Přetáhněte<xref:System.Activities.Statements.WriteLine> za aktivitu. Aktivitu najdete v části pro zasílání **zpráv** v **sadě nástrojů.** <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivita se skládá ze dvou částí **žádosti** a **textu.** <xref:System.ServiceModel.Activities.TransactedReceiveScope> Část **žádosti** obsahuje <xref:System.ServiceModel.Activities.Receive> aktivitu. Oddíl **text** obsahuje aktivity, které se mají provést v rámci transakce po přijetí zprávy.  
  
     ![Přidání aktivity TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Vyberte aktivitu a klikněte na tlačítko **proměnné.** <xref:System.ServiceModel.Activities.TransactedReceiveScope> Přidejte následující proměnné.  
  
     ![Přidávání proměnných do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Můžete odstranit datovou proměnnou, která je ve výchozím nastavení. Můžete také použít existující proměnnou popisovače.  
  
6. Přetáhněte aktivitu v části <xref:System.ServiceModel.Activities.TransactedReceiveScope> žádosti aktivity. <xref:System.ServiceModel.Activities.Receive> Nastavte následující vlastnosti:  
  
    |Vlastnost|Value|  
    |--------------|-----------|  
    |CanCreateInstance|Pravda (zaškrtněte políčko)|  
    |OperationName|StartSample|  
    |Stejnými ServiceContractName|ITransactionSample|  
  
     Pracovní postup by měl vypadat takto:  
  
     ![Přidání aktivity Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. V<xref:System.ServiceModel.Activities.Receive> aktivitě klikněte na odkaz **definovat...** a proveďte následující nastavení:  
  
     ![Nastavení nastavení zpráv pro aktivitu Receive](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Přetáhněte aktivitu do části text v <xref:System.ServiceModel.Activities.TransactedReceiveScope>. <xref:System.Activities.Statements.Sequence> V rámci <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.WriteLine.Text%2A> aktivity přetahujte a přetáhněte dvě aktivity a nastavte vlastnosti, jak je znázorněno v následující tabulce. <xref:System.Activities.Statements.Sequence>  
  
    |Aktivita|Value|  
    |--------------|-----------|  
    |1\. WriteLine|Službám Přijetí dokončeno|  
    |druhý WriteLine|Službám Přijato = "+ requestMessage|  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Sekvence po přidání aktivit WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Přetáhněte aktivitu za druhou <xref:System.Activities.Statements.WriteLine> aktivitu <xref:System.ServiceModel.Activities.TransactedReceiveScope> v těle aktivity. `PrintTransactionInfo`  
  
     ![Sekvence po přidání PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <xref:System.Activities.Statements.Assign> Přetáhněte aktivitu`PrintTransactionInfo` za aktivitu a nastavte její vlastnosti podle následující tabulky.  
  
    |Vlastnost|Value|  
    |--------------|-----------|  
    |Chcete-li|replyMessage|  
    |Value|Službám Posílá se odpověď.|  
  
11. Přetáhněte aktivitu za aktivitou a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "Service: <xref:System.Activities.Statements.Assign> <xref:System.Activities.Statements.WriteLine> Zahajte odpověď.  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Po přidání přiřadit a odwriteline](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Klikněte pravým <xref:System.ServiceModel.Activities.Receive> tlačítkem na aktivitu a vyberte **vytvořit aktivitu SendReply** a vložte ji <xref:System.Activities.Statements.WriteLine> za poslední aktivitu. V`SendReplyToReceive` aktivitě klikněte na odkaz **definovat...** a proveďte následující nastavení.  
  
     ![Nastavení zprávy s odpovědí](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Přetáhněte aktivitu za `SendReplyToReceive` aktivitou a nastavte její vlastnostna"služba:<xref:System.Activities.Statements.WriteLine.Text%2A> <xref:System.Activities.Statements.WriteLine> Odeslala se odpověď. "  
  
14. Přetáhněte aktivitu do dolní části pracovního postupu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "Service: <xref:System.Activities.Statements.WriteLine> Pracovní postup skončí, stisknutím klávesy ENTER ukončete. "  
  
     Dokončený pracovní postup služby by měl vypadat takto:  
  
     ![Dokončení pracovního postupu služby](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Implementace klienta pracovního postupu  
  
1. Přidejte novou aplikaci pracovního postupu WCF, `WorkflowClient` `Common` která se volá do projektu. Chcete-li to provést, `Common` klikněte pravým tlačítkem myši na projekt, vyberte možnost **Přidat**, **Nová položka...** , vyberte možnost **pracovní postup** v části **Nainstalované šablony** a vyberte **aktivita**.  
  
     ![Přidat projekt aktivity](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <xref:System.Activities.Statements.Sequence> Přetáhněte aktivitu na návrhovou plochu.  
  
3. V rámci <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.WriteLine.Text%2A> aktivity přetáhněte aktivitu a nastavte její vlastnost na `"Client: Workflow starting"`. <xref:System.Activities.Statements.Sequence> Pracovní postup by teď měl vypadat takto:  
  
     ![Přidání aktivity WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <xref:System.Activities.Statements.TransactionScope> Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> za aktivitou.  <xref:System.Activities.Statements.TransactionScope> Vyberte aktivitu, klikněte na tlačítko proměnné a přidejte následující proměnné.  
  
     ![Přidat proměnné do objektu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Přetáhněte aktivitu do těla <xref:System.Activities.Statements.TransactionScope>aktivity. <xref:System.Activities.Statements.Sequence>  
  
6. `PrintTransactionInfo` Přetáhněte aktivitu v rámci<xref:System.Activities.Statements.Sequence>  
  
7. Přetáhněte aktivitu za aktivitou a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "klient: `PrintTransactionInfo` <xref:System.Activities.Statements.WriteLine> Začíná se odesílat. Pracovní postup by teď měl vypadat takto:  
  
     ![Přidávání klienta: Zahájení aktivit odeslání](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <xref:System.ServiceModel.Activities.Send> Přetáhněte aktivitu<xref:System.Activities.Statements.Assign> za aktivitu a nastavte následující vlastnosti:  
  
    |Vlastnost|Value|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |Stejnými ServiceContractName|ITransactionSample|  
  
     Pracovní postup by teď měl vypadat takto:  
  
     ![Nastavení vlastností aktivity odeslání](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Klikněte na odkaz **definovat...** a proveďte následující nastavení:  
  
     ![Odeslat nastavení zprávy o aktivitě](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Klikněte pravým <xref:System.ServiceModel.Activities.Send> tlačítkem na aktivitu a vyberte **vytvořit ReceiveReply**. Aktivita se automaticky umístí <xref:System.ServiceModel.Activities.Send> za aktivitu. <xref:System.ServiceModel.Activities.ReceiveReply>  
  
11. Klikněte na definovat... Propojte aktivitu ReceiveReplyForSend a proveďte následující nastavení:  
  
     ![Nastavení zprávy ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Přetáhněte aktivitu mezi aktivitami <xref:System.ServiceModel.Activities.ReceiveReply>aa nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na Client: <xref:System.ServiceModel.Activities.Send> <xref:System.Activities.Statements.WriteLine> Odeslat dokončeno. "  
  
13. Přetáhněte aktivitu za aktivitou a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na stranu klienta: <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.Activities.Statements.WriteLine> Přijatá odpověď = "+ replyMessage  
  
14. `PrintTransactionInfo` Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> za aktivitou.  
  
15. Přetáhněte aktivitu na konci pracovního postupu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "pracovní postup klienta končí." <xref:System.Activities.Statements.WriteLine> Dokončený pracovní postup klienta by měl vypadat jako v následujícím diagramu.  
  
     ![Dokončený pracovní postup klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Sestavte řešení.  
  
### <a name="create-the-service-application"></a>Vytvoření aplikace služby  
  
1. Přidejte do řešení nový projekt konzolové `Service` aplikace s názvem. Přidejte odkazy na následující sestavení:  
  
    1. System.Activities.dll  
  
    2. System.ServiceModel.dll  
  
    3. System.ServiceModel.Activities.dll  
  
2. Otevřete vygenerovaný soubor Program.cs a následující kód:  
  
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
  
1. Přidejte do řešení nový projekt konzolové `Client` aplikace s názvem. Přidejte odkaz na System. Activities. dll.  
  
2. Otevřete soubor program.cs a přidejte následující kód.  
  
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
