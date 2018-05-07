---
title: Aktivity zasílání zpráv
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 1ae03b1671aa5c938bb3897edb919643f795f8a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="messaging-activities"></a>Aktivity zasílání zpráv
Zasílání zpráv aktivity umožňují pracovní postupy pro odesílání a přijímání zpráv WCF. Přidáním aktivity zasílání zpráv do pracovního postupu můžete model žádné libovolně komplexní zpráva exchange vzory (MEP).  
  
## <a name="message-exchange-patterns"></a>Vzory Exchange zpráv  
 Existují tři vzory exchange základní zpráva:  
  
-   **Datagram** – při použití datagram MEP klient odešle zprávu do služby, ale služba nereaguje. To se někdy nazývá "fire a zapomněli". A fire a zapomněli exchange je ten, který vyžaduje out-of-band potvrzení úspěšné doručení. Zpráva může dojít ke ztrátě během přenosu a nikdy nedorazí službu. Pokud klient úspěšně odešle zprávu, není zaručeno, že Služba obdržela zprávu. Datagram je základní stavební blok pro zasílání zpráv, jak můžete vytvořit vlastní MEPs nad ho.  
  
-   **Požadavků a odpovědí** – když pomocí požadavků a odpovědí MEP klient odešle zprávu, která službu, službu nemá požadované zpracování, a pak zasílá odpověď zpět klientovi. Vzor se skládá z dvojice požadavků a odpovědí. Příkladem volání požadavků a odpovědí jsou vzdálených volání procedur (RPC) a prohlížeče GET požadavky. Tento vzor se také označuje jako poloduplexní.  
  
-   **Duplexní** – při použití duplexní MEP klienta a služby mohou zasílat zprávy do sebe navzájem v libovolném pořadí. Duplexní MEP je třeba je telefonní hovor, kde je jednotlivých slov použitém zprávu.  
  
 Zasílání zpráv aktivity umožňují implementovat některé z těchto základní MEPs i jakékoli libovolně komplexní MEP.  
  
## <a name="messaging-activities"></a>Aktivity zasílání zpráv  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Definuje následující zasílání zpráv aktivity:  
  
-   <xref:System.ServiceModel.Activities.Send>-Použít <xref:System.ServiceModel.Activities.Send> aktivity odeslat zprávu.  
  
-   <xref:System.ServiceModel.Activities.SendReply> -Použít <xref:System.ServiceModel.Activities.SendReply> aktivity pro odesílání odpovědí na přijatou zprávu. Tato aktivita používá služby pracovního postupu při implementaci požadavek nebo odpověď MEP.  
  
-   <xref:System.ServiceModel.Activities.Receive>-Použít <xref:System.ServiceModel.Activities.Receive> aktivity pro příjem zprávy.  
  
-   <xref:System.ServiceModel.Activities.ReceiveReply> -Použít <xref:System.ServiceModel.Activities.ReceiveReply> aktivity pro příjem zprávy odpovědi. Tato aktivita se používají klienti služby pracovního postupu při implementaci požadavek nebo odpověď MEP.  
  
## <a name="messaging-activities-and-message-exchange-patterns"></a>Aktivity zasílání zpráv a vzory Exchange zpráv  
 Datagram MEP zahrnuje klient odesílá zprávy a služby danou zprávu přijala. Pokud je klient použití pracovního postupu <xref:System.ServiceModel.Activities.Send> aktivity odeslat zprávu. Chcete-li přijímat zprávy v pracovním postupu, použijte <xref:System.ServiceModel.Activities.Receive> aktivity. <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> aktivity každý mít vlastnost s názvem `Content`. Tato vlastnost obsahuje data se odesílané nebo přijímané. Při implementaci MEP požadavků a odpovědí klienta a službu používají dvojice aktivit. Klient použije <xref:System.ServiceModel.Activities.Send> aktivity odeslat zprávu a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity získat odpověď ze služby. Tyto dvě aktivity jsou spojeny s jinými pomocí <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> vlastnost. Tato vlastnost nastavena na <xref:System.ServiceModel.Activities.Send> aktivity, která původní zprávu odeslala. Služba také používá pár přidružené aktivit: <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>. Tyto dvě aktivity jsou přidružené pomocí <xref:System.ServiceModel.Activities.SendReply.Request%2A> vlastnost. Tato vlastnost nastavena na <xref:System.ServiceModel.Activities.Receive> aktivity, která zobrazila původní zprávy. <xref:System.ServiceModel.Activities.ReceiveReply> a <xref:System.ServiceModel.Activities.SendReply> aktivity, jako například <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> vám umožní odesílat <xref:System.ServiceModel.Channels.Message> instance nebo zprávu typ kontraktu.  
  
 Dlouhodobé charakter pracovních postupů je důležité pro vzoru duplexní komunikace podporuje taky dlouho běžící konverzace. Pro podporu dlouhodobé konverzace, klienti, kteří zahájit konverzaci musí poskytnout službu příležitost zpětné volání v pozdějším čase, kdy budou data k dispozici. Například je odeslána žádost pořadí nákupu pro schválení správce, ale nemusí být zpracovány za den, týden nebo i v roce; pracovní postup, který spravuje schválení nákupní objednávky musí znát po schválení lze obnovit. Tento vzor duplexní komunikace je podporována v pracovních postupech, pomocí korelace. Chcete-li implementovat duplexní vzor, použijte <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> aktivity. Na <xref:System.ServiceModel.Activities.Receive> aktivity, inicializovat a korelace pomocí speciální klíčovou hodnotu <!--zz <xref:System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName%2A>--> `System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName`. Na <xref:System.ServiceModel.Activities.Send> aktivity nastavený popisovače korelace jako <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> hodnotu vlastnosti. Další informace najdete v tématu [trvanlivý duplexní](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md).  
  
> [!NOTE]
>  Implementace pracovního postupu pomocí existuje korelace zpětného volání ("trvanlivý duplexní") duplexní režim je určený pro dlouhodobé konverzace. Toto není stejný jako WCF duplexní s kontrakty zpětného volání kde konverzace je krátké běžící (životnost kanál).  
  
## <a name="message-formatting-and-messaging-activities"></a>Formátování zprávy a aktivity zasílání zpráv  
 <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity mají vlastnost s názvem `Content`. Tato vlastnost je typu <xref:System.ServiceModel.Activities.ReceiveContent> a představuje data <xref:System.ServiceModel.Activities.Receive> nebo <xref:System.ServiceModel.Activities.ReceiveReply> obdrží aktivity. Rozhraní .NET Framework definuje dvě související třídy názvem <xref:System.ServiceModel.Activities.ReceiveMessageContent> a <xref:System.ServiceModel.Activities.ReceiveParametersContent> které jsou odvozeny od <xref:System.ServiceModel.Activities.ReceiveContent>. Nastavte <xref:System.ServiceModel.Activities.Receive> nebo <xref:System.ServiceModel.Activities.ReceiveReply> aktivity `Content` vlastnost, která má instance jednoho z těchto typů přijímat data do služby pracovních postupů. Typ určený k použití závisí na typu dat, které obdrží aktivity. Pokud aktivita přijme `Message` objekt nebo zprávu typ kontraktu, použijte <xref:System.ServiceModel.Activities.ReceiveMessageContent>. Pokud aktivita obdrží sady kontraktu dat nebo typy XML, které lze serializovat, použijte <xref:System.ServiceModel.Activities.ReceiveParametersContent>. <xref:System.ServiceModel.Activities.ReceiveParametersContent> umožní vám odesílat několik parametrů, zatímco <xref:System.ServiceModel.Activities.ReceiveMessageContent> lze pouze jeden objekt odeslání, zprávy (nebo typ kontrakt zprávy).  
  
> [!NOTE]
>  <xref:System.ServiceModel.Activities.ReceiveMessageContent> Můžete také použít kontrakt jeden dat nebo typ XML, který lze serializovat. Rozdíl mezi použitím <xref:System.ServiceModel.Activities.ReceiveParametersContent> s jeden parametr a objekt předaný přímo <xref:System.ServiceModel.Activities.ReceiveMessageContent> je přenosový formát. Obsah parametr je uzavřen do elementu XML, který odpovídá názvu operace a serializovaný objekt je uzavřen do elementu XML s použitím názvu parametru (například `<Echo><msg>Hello, World</msg></Echo>`). Obsah zprávy není zabalen název operace. Místo toho serializovaný objekt je umístěn v rámci elementu XML pomocí názvu XML kvalifikovaný typ (například `<string>Hello, World</string>`).  
  
 <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.SendReply> aktivity mají také vlastnost s názvem `Content`. Tato vlastnost je typu <xref:System.ServiceModel.Activities.SendContent> a představuje data <xref:System.ServiceModel.Activities.Send> nebo <xref:System.ServiceModel.Activities.SendReply> zasílá aktivity. Rozhraní .NET Framework definuje dva typy související názvem <xref:System.ServiceModel.Activities.SendMessageContent> a <xref:System.ServiceModel.Activities.SendParametersContent> které jsou odvozeny od <xref:System.ServiceModel.Activities.SendContent>. Nastavte <xref:System.ServiceModel.Activities.Send> nebo <xref:System.ServiceModel.Activities.SendReply> aktivity `Content` vlastnost, která má instance jednoho z těchto typů odeslat data ze služby pracovních postupů. Typ určený k použití závisí na typu dat, které odesílá aktivity. Pokud aktivita odesílá `Message` objekt nebo zprávu typ kontraktu, použijte <xref:System.ServiceModel.Activities.SendMessageContent>. Pokud aktivita odesílá k využívání typu kontraktu dat <xref:System.ServiceModel.Activities.SendParametersContent>. <xref:System.ServiceModel.Activities.SendParametersContent> umožní vám odesílat několik parametrů, zatímco <xref:System.ServiceModel.Activities.SendMessageContent> pouze umožní vám odesílat jeden objekt, zprávy (nebo typ kontrakt zprávy).  
  
 Při programování imperativní s zasílání zpráv aktivity, je použít Obecné <xref:System.Activities.InArgument%601> a <xref:System.Activities.OutArgument%601> zabalit objekty přiřadit vlastnosti zprávy nebo parametry <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive>a <xref:System.ServiceModel.Activities.ReceiveReply>aktivity. Použití <xref:System.Activities.InArgument%601> pro <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.SendReply> aktivity a <xref:System.Activities.OutArgument%601> pro <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. `In` argumenty se používají v aktivitách odeslat, protože data je předávána do aktivity. `Out` argumenty se používají v aktivitách receive, protože data je předávána mimo aktivity, jak je znázorněno v následujícím příkladu.  
  
```  
Receive reserveSeat = new Receive  
{   
    ...   
    Content = new ReceiveParametersContent  
    {  
        Parameters =  
        {  
            { "ReservationInfo", new OutArgument<ReservationRequest>(reservationInfo) }  
        }  
    }  
};  
SendReply reserveSeat = new SendReply  
{   
    ...   
    Request = reserveSeat,  
    Content = new SendParametersContent  
    {  
        Parameters =  
        {  
            { "ReservationId", new InArgument<string>(reservationId) }  
        }  
    },  
};  
```  
  
 Při implementaci Služba pracovního postupu, která definuje operace požadavků a odpovědí, který vrací void, je třeba vytvořit instanci <xref:System.ServiceModel.Activities.SendReply> aktivity a sady <xref:System.ServiceModel.Activities.SendReply.Content%2A> vlastnost, která má prázdnou instanci jednoho z typů obsahu (<xref:System.ServiceModel.Activities.SendMessageContent> nebo <xref:System.ServiceModel.Activities.SendParametersContent>) jak je znázorněno v následujícím příkladu.  
  
```  
Receive rcv = new Receive()  
{  
ServiceContractName = "IService",  
OperationName = "NullReturningContract",  
Content = new ReceiveParametersContent( new Dictionary<string, OutArgument>() { { "message", new OutArgument<string>() } } )  
};  
SendReply sr = new SendReply()  
{  
Request = rcv  
   Content = new SendParametersContent();  
};  
```  
  
## <a name="add-service-reference"></a>Přidání odkazu na službu  
 Při volání služby pracovního postupu z aplikace pracovního postupu, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] generuje vlastní aktivity zasílání zpráv, které zapouzdření obvykle <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivit používaných v požadavku/odpovědi MEP. Chcete-li použít tuto funkci, klikněte pravým tlačítkem projektu klienta v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] a vyberte **přidat odkaz na službu**. Zadejte základní adresu služby do pole Adresa a kliknutím na Přejít. K dispozici služby se zobrazí v **služby:** pole. Rozbalte uzel služby zobrazíte kontrakty podporována. Zvolte smlouvu, kterou chcete volat a zobrazí se seznam dostupných operací v **Operations** pole. Potom můžete zadat obor názvů pro generovaný aktivity a klikněte na tlačítko **OK**. Zobrazí se dialogové okno, které uvádí operace byla úspěšně dokončena a jestli je vygenerovaný vlastní aktivity v sadě nástrojů po znovu sestavit projekt. Je jedna aktivita pro každou operaci definovaný pro kontrakt služby. Po projekt znovu sestavit můžete můžete přetahování vlastních aktivit do pracovního postupu a nastavit jakékoliv nezbytné vlastnosti, v okně Vlastnosti.  
  
<!--## Messaging Activity Templates  
 To make setting up a request/response MEP on the client and service easier, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] provides two messaging activity templates. <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> is used on the service and <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> is used on the client. In both cases the templates add the appropriate messaging activities to your workflow. On the service, the <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> adds a <xref:System.ServiceModel.Activities.Receive> activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity. The <xref:System.ServiceModel.Activities.SendReply.Request> property is automatically set to the <xref:System.ServiceModel.Activities.Receive> activity. On the client, the <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> adds a <xref:System.ServiceModel.Activities.Send> activity followed by a <xref:System.ServiceModel.Activities.ReceiveReply>. The <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> property is automatically set to the <xref:System.ServiceModel.Activities.Send> activity. To use these templates, just drag and drop the appropriate template onto your workflow.  
-->
## <a name="messaging-activities-and-transactions"></a>Aktivity zasílání zpráv a transakce  
 Při volání služby pracovního postupu můžete toku transakci operaci služby. Chcete toto místo <xref:System.ServiceModel.Activities.Receive> aktivita v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Obsahuje aktivitu `Receive` aktivity a text. Transakce předávány vedlejším v průběhu provádění textu služby zůstane <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Transakce byla dokončena, když text dokončí provádění. Další informace o pracovních postupů a transakce v tématu [pracovního postupu transakce](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md).  
  
## <a name="see-also"></a>Viz také  
 [Jak odesílat a přijímat chyb v služeb pracovních postupů](http://go.microsoft.com/fwlink/?LinkId=189151)  
 [Vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
