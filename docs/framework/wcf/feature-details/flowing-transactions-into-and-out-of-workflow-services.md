---
title: Tok transakcí do služeb pracovních postupů a mimo ně
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 8b3d3e85b626d033c9ab50e93e3ceb3b86058a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496094"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Tok transakcí do služeb pracovních postupů a mimo ně
Pracovní postup služby a klienti mohou účastnit transakce.  Pro operaci služby, který se stane součástí vedlejším transakce, umístit <xref:System.ServiceModel.Activities.Receive> aktivita v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. Volání pomocí <xref:System.ServiceModel.Activities.Send> nebo <xref:System.ServiceModel.Activities.SendReply> aktivita v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> bude také provést v rámci vedlejším transakce. Klientská aplikace pracovního postupu můžete vytvořit pomocí vedlejším transakce <xref:System.Activities.Statements.TransactionScope> aktivity a volání operací služby pomocí vedlejším transakce. Toto téma vás provede procesem vytvoření služby pracovního postupu a pracovní postup klienta, které se začlení transakcí.  
  
> [!WARNING]
>  Pokud je v rámci transakce načíst instanci pracovního postupu služby a pracovní postup obsahuje <xref:System.Activities.Statements.Persist> aktivity, instance pracovního postupu se zablokuje, dokud transakce časového limitu.  
  
> [!IMPORTANT]
>  Vždy, když používáte <xref:System.ServiceModel.Activities.TransactedReceiveScope> doporučujeme umístit všechny Receives v pracovním postupu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.  
  
> [!IMPORTANT]
>  Při použití <xref:System.ServiceModel.Activities.TransactedReceiveScope> a doručování zpráv v nesprávném pořadí, pracovní postup bude přerušena při pokusu o doručení první zprávy mimo pořadí. Je nutné zajistěte, aby že pracovní postup je vždy na jednotnou zastavování bod při pracovního postupu nečinné po dlouhou dobu. Bude možné restartovat pracovní postup z předchozího bodu trvalost přerušena pracovního postupu.  
  
### <a name="create-a-shared-library"></a>Vytvoření sdílené knihovny  
  
1.  Vytvoření nové prázdné Visual Studio řešení.  
  
2.  Přidat nový projekt knihovny třídy s názvem `Common`. Přidejte odkazy na následující sestavení:  
  
    -   System.Activities.dll  
  
    -   System.ServiceModel.dll  
  
    -   System.ServiceModel.Activities.dll  
  
    -   System.Transactions.dll  
  
3.  Přidejte novou třídu s názvem `PrintTransactionInfo` k `Common` projektu. Tato třída je odvozený od <xref:System.Activities.NativeActivity> a přetížení <xref:System.Activities.NativeActivity.Execute%2A> metoda.  
  
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
  
     Toto je nativní aktivity, která zobrazuje informace o vedlejším transakce a používá se v pracovních postupech služby i klient použitým v tomto tématu. Sestavte řešení Chcete-li k dispozici v této aktivity **běžné** části **sada nástrojů**.  
  
### <a name="implement-the-workflow-service"></a>Implementace služby pracovního postupu  
  
1.  Přidání nové služby pracovního postupu WCF, nazývá `WorkflowService` k `Common` projektu. Na pravé tlačítko `Common` projekt, vyberte **přidat**, **novou položku...** , Vyberte **pracovního postupu** pod **nainstalovaných šablonách** a vyberte **pracovního postupu služby WCF**.  
  
     ![Přidání služby pracovního postupu](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")  
  
2.  Odstranit výchozí `ReceiveRequest` a `SendResponse` aktivity.  
  
3.  Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity do `Sequential Service` aktivity. Nastavte vlastnost text na `"Workflow Service starting ..."` jak je znázorněno v následujícím příkladu.  
  
     ![Přidání aktivity WriteLine](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")  
  
4.  Přetáhnout myší <xref:System.ServiceModel.Activities.TransactedReceiveScope> po <xref:System.Activities.Statements.WriteLine> aktivity. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivity naleznete v **zasílání zpráv** části **sada nástrojů**. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivity se skládá ze dvou částech **požadavku** a **textu**. **Požadavku** část obsahuje <xref:System.ServiceModel.Activities.Receive> aktivity. **Textu** část obsahuje aktivity po byla přijata zpráva provést v transakci.  
  
     ![Přidání aktivity TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")  
  
5.  Vyberte <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity a klikněte na **proměnné** tlačítko. Přidejte následující proměnné.  
  
     ![Přidání proměnné do TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")  
  
    > [!NOTE]
    >  Proměnné data, která je k dispozici ve výchozím nastavení, můžete odstranit. Můžete také použít existující proměnnou popisovač.  
  
6.  Přetáhnout myší <xref:System.ServiceModel.Activities.Receive> aktivita v rámci **požadavku** části <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. Nastavte následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |CanCreateInstance|Hodnotu true (zaškrtávací políčko)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Pracovní postup by měl vypadat takto:  
  
     ![Přidání aktivity Receive](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")  
  
7.  Klikněte **definovat...**  odkaz <xref:System.ServiceModel.Activities.Receive> aktivity a proveďte následující nastavení:  
  
     ![Nastavení zprávy pro aktivitu Receive](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")  
  
8.  Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity do části textu <xref:System.ServiceModel.Activities.TransactedReceiveScope>. V rámci <xref:System.Activities.Statements.Sequence> aktivity přetažení dva <xref:System.Activities.Statements.WriteLine> aktivity a sady <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnosti, jak je znázorněno v následující tabulce.  
  
    |Aktivita|Hodnota|  
    |--------------|-----------|  
    |WriteLine 1.|"Service: přijímat dokončené"|  
    |WriteLine 2.|"Service: přijaté =" + requestMessage|  
  
     Pracovní postup by měl nyní vypadat takto:  
  
     ![Přidání aktivity WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")  
  
9. Přetáhnout myší `PrintTransactionInfo` aktivity po druhá <xref:System.Activities.Statements.WriteLine> aktivity v **textu** v <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.  
  
     ![Po přidání PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")  
  
10. Přetáhnout myší <xref:System.Activities.Statements.Assign> aktivity po `PrintTransactionInfo` aktivity a nastavit jeho vlastnosti podle následující tabulky.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |Chcete-li|replyMessage|  
    |Hodnota|"Service: odeslání odpovědi."|  
  
11. Přetažení <xref:System.Activities.Statements.WriteLine> aktivity po <xref:System.Activities.Statements.Assign> aktivity a sady jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Service: začít odpovědi."  
  
     Pracovní postup by měl nyní vypadat takto:  
  
     ![Po přidání přiřazení a WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")  
  
12. Klikněte pravým tlačítkem <xref:System.ServiceModel.Activities.Receive> aktivitu a vyberte **vytvořit SendReply** a vložte ji za poslední <xref:System.Activities.Statements.WriteLine> aktivity. Klikněte **definovat...**  odkaz `SendReplyToReceive` aktivity a proveďte následující nastavení.  
  
     ![Odpovědět nastavení zpráv](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")  
  
13. Přetažení <xref:System.Activities.Statements.WriteLine> aktivity po `SendReplyToReceive` aktivity a sady má <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Service: odpověď odeslaná."  
  
14. Přetažení <xref:System.Activities.Statements.WriteLine> aktivity na konci pracovního postupu a sadu jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost, která má "Service: ukončení pracovního postupu, stiskněte klávesu ENTER, chcete-li ukončit."  
  
     Dokončené služby pracovního postupu by měl vypadat takto:  
  
     ![Dokončení pracovního postupu služby](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")  
  
### <a name="implement-the-workflow-client"></a>Implementace klienta pracovního postupu  
  
1.  Přidejte novou aplikaci WCF pracovního postupu, s názvem `WorkflowClient` k `Common` projektu. Na pravé tlačítko `Common` projekt, vyberte **přidat**, **novou položku...** , Vyberte **pracovního postupu** pod **nainstalovaných šablonách** a vyberte **aktivity**.  
  
     ![Přidání aktivity projektu](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")  
  
2.  Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity na návrhovou plochu.  
  
3.  V rámci <xref:System.Activities.Statements.Sequence> aktivity přetažení <xref:System.Activities.Statements.WriteLine> aktivity a sady jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost `"Client: Workflow starting"`. Pracovní postup by měl nyní vypadat takto:  
  
     ![Přidat aktivitu WriteLine](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")  
  
4.  Přetáhnout myší <xref:System.Activities.Statements.TransactionScope> aktivity po <xref:System.Activities.Statements.WriteLine> aktivity.  Vyberte <xref:System.Activities.Statements.TransactionScope> aktivity, klikněte na tlačítko proměnné a přidejte následující proměnné.  
  
     ![Přidání proměnné do v objektu TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")  
  
5.  Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity do textu <xref:System.Activities.Statements.TransactionScope> aktivity.  
  
6.  Přetáhnout myší `PrintTransactionInfo` aktivita v rámci <xref:System.Activities.Statements.Sequence>  
  
7.  Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po `PrintTransactionInfo` aktivity a sady jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Klienta: začátku odeslat". Pracovní postup by měl nyní vypadat takto:  
  
     ![Přidání aktivity](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")  
  
8.  Přetáhnout myší <xref:System.ServiceModel.Activities.Send> aktivity po <xref:System.Activities.Statements.Assign> aktivity a nastavte následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Pracovní postup by měl nyní vypadat takto:  
  
     ![Nastavení vlastnosti Send aktivity](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")  
  
9. Klikněte **definovat...**  propojit a proveďte následující nastavení:  
  
     ![Odeslat zprávu nastavení aktivity](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")  
  
10. Klikněte pravým tlačítkem <xref:System.ServiceModel.Activities.Send> aktivitu a vyberte **vytvořit ReceiveReply**. <xref:System.ServiceModel.Activities.ReceiveReply> Aktivity se po automaticky umístí <xref:System.ServiceModel.Activities.Send> aktivity.  
  
11. Klikněte na možnost definovat... odkaz na ReceiveReplyForSend aktivity a proveďte následující nastavení:  
  
     ![Nastavení zpráv ReceiveForSend](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")  
  
12. Přetažení <xref:System.Activities.Statements.WriteLine> aktivity mezi <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity a sady jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "klienta: dokončení odesílání."  
  
13. Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po <xref:System.ServiceModel.Activities.ReceiveReply> aktivity a sady jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnosti "na straně klienta: odpověď přijata =" + replyMessage  
  
14. Přetáhnout myší `PrintTransactionInfo` aktivity po <xref:System.Activities.Statements.WriteLine> aktivity.  
  
15. Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity na konci pracovního postupu a sadu jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Klienta pracovního postupu zakončením." Pracovní postup dokončené klienta by měl vypadat jako na následujícím diagramu.  
  
     ![Dokončené klienta workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")  
  
16. Sestavte řešení.  
  
### <a name="create-the-service-application"></a>Vytvořit aplikaci služby  
  
1.  Přidat nový projekt konzolové aplikace s názvem `Service` k řešení. Přidejte odkazy na následující sestavení:  
  
    1.  System.Activities.dll  
  
    2.  System.ServiceModel.dll  
  
    3.  System.ServiceModel.Activities.dll  
  
2.  Otevřete generovaný soubor Program.cs a následující kód:  
  
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
  
### <a name="create-the-client-application"></a>Vytvoření aplikace klienta  
  
1.  Přidat nový projekt konzolové aplikace s názvem `Client` k řešení. Přidáte odkaz na System.Activities.dll.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Přehled transakcí ve Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/transactions-overview.md)  
 [Použití TransactedReceiveScope](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)
