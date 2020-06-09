---
title: Aktivity zasílání zpráv
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 69a0e9a415b10d9c58d04eac27e48b1ed6a78064
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576392"
---
# <a name="messaging-activities"></a>Aktivity zasílání zpráv

Aktivity zasílání zpráv umožňují pracovním postupům odesílat a přijímat zprávy WCF. Přidáním aktivit zasílání zpráv do pracovního postupu můžete modelovat libovolně složité vzory výměny zpráv (MEP).

## <a name="message-exchange-patterns"></a>Vzorce výměny zpráv

Existují tři základní vzorce výměny zpráv:

- **Datagram** – při použití datagramu MEP odešle klient zprávu službě, ale služba nereaguje. Tato situace se někdy označuje jako "oheň" a "zapomenout". Výměna požáru a zapomenutí je taková, která vyžaduje vzdálené potvrzení úspěšného doručení. Zpráva může být ztracena při přenosu a nikdy se nespojit se službou. Pokud klient úspěšně pošle zprávu, nezaručuje, že služba obdržela zprávu. Datagram je základní stavební blok pro zasílání zpráv, protože můžete vytvořit vlastní MEPs nad ním.

- **Požadavek-odpověď** – při použití požadavku-Response MEP klient pošle zprávu službě, služba provede požadované zpracování a pak pošle odpověď zpátky klientovi. Vzor se skládá z párů požadavků a odpovědí. Příklady volání požadavků na odezvu jsou vzdálená volání procedur (RPC) a požadavky GET prohlížeče. Tento model se také označuje jako poloduplexní.

- **Duplexní** – při použití duplexního MEP může klient a služba posílat zprávy v libovolném pořadí. Duplexní MEP je jako telefonická konverzace, kde každé mluvené slovo je zpráva.

Aktivity zasílání zpráv umožňují implementovat některé z těchto základních MEPs a také libovolně komplexní MEP.

## <a name="messaging-activities"></a>Aktivity zasílání zpráv

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]Definuje následující aktivity zasílání zpráv:

- <xref:System.ServiceModel.Activities.Send>– <xref:System.ServiceModel.Activities.Send> K odeslání zprávy použijte aktivitu.

- <xref:System.ServiceModel.Activities.SendReply>– <xref:System.ServiceModel.Activities.SendReply> K odeslání odpovědi na přijatou zprávu použijte aktivitu. Tuto aktivitu používají služby pracovních postupů při implementaci MEP požadavků a odpovědí.

- <xref:System.ServiceModel.Activities.Receive>– <xref:System.ServiceModel.Activities.Receive> K přijetí zprávy použijte aktivitu.

- <xref:System.ServiceModel.Activities.ReceiveReply>– Použijte <xref:System.ServiceModel.Activities.ReceiveReply> aktivitu pro příjem zprávy s odpovědí. Tuto aktivitu používají klienti služby pracovního postupu při implementaci MEP požadavků a odpovědí.

## <a name="messaging-activities-and-message-exchange-patterns"></a>Aktivity zasílání zpráv a vzory výměny zpráv

Datagram MEP zahrnuje klienta odesílajícího zprávu a službu přijímající zprávu. Pokud je klient pracovní postup, použijte <xref:System.ServiceModel.Activities.Send> aktivitu k odeslání zprávy. Pokud chcete tuto zprávu přijmout v pracovním postupu, použijte <xref:System.ServiceModel.Activities.Receive> aktivitu. <xref:System.ServiceModel.Activities.Send>Aktivity a <xref:System.ServiceModel.Activities.Receive> obsahují vlastnost s názvem `Content` . Tato vlastnost obsahuje data odesílaná nebo přijímaná. Když implementujete požadavek-Response MEP, klient i služba používají páry aktivit. Klient používá <xref:System.ServiceModel.Activities.Send> aktivitu k odeslání zprávy a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity k přijetí odpovědi ze služby. Tyto dvě aktivity jsou vzájemně spojeny <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> vlastností. Tato vlastnost je nastavena na <xref:System.ServiceModel.Activities.Send> aktivitu, která odeslala původní zprávu. Služba používá také dvojici přidružených aktivit: <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> . Tyto dvě aktivity jsou přidruženy <xref:System.ServiceModel.Activities.SendReply.Request%2A> vlastností. Tato vlastnost je nastavena na <xref:System.ServiceModel.Activities.Receive> aktivitu, která přijala původní zprávu. <xref:System.ServiceModel.Activities.ReceiveReply>Aktivity a <xref:System.ServiceModel.Activities.SendReply> , jako <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> umožňují odeslat <xref:System.ServiceModel.Channels.Message> instanci nebo typ kontraktu zprávy.

Z důvodu dlouhotrvajícího chodu pracovních postupů je důležité, aby duplexní vzor komunikace podporoval i dlouhotrvající konverzace. Aby bylo možné podporovat dlouhotrvající konverzace, klienti, kteří iniciují konverzaci, musí poskytovat službu s příležitostí k pozdějšímu volání, když budou data k dispozici. Například žádost o nákupní objednávku je odeslána ke schválení vedoucího, ale nemusí být zpracována za den, týden nebo dokonce rok; pracovní postup, který spravuje schválení nákupních objednávek, musí znát, aby se obnovil i po tom, co bylo schválení uděleno. Tento vzor duplexních komunikací je podporován v pracovních postupech pomocí korelace. K implementaci duplexního vzoru, použijte <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> aktivity a. V <xref:System.ServiceModel.Activities.Receive> aktivitě inicializujte korelační pomocí <xref:System.ServiceModel.Activities.CorrelationHandle> . V <xref:System.ServiceModel.Activities.Send> sadě aktivit, kterou korelační zpracuje jako <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> hodnotu vlastnosti. Další informace najdete v tématu [trvalé duplexní přenos](durable-duplex-correlation.md).

> [!NOTE]
> Implementace oboustranného pracovního postupu pomocí korelace zpětného volání ("trvanlivé duplexní") je určená pro dlouhotrvající konverzace. Nejedná se o stejný jako duplexní přenos WCF se kontrakty zpětného volání, kde je konverzace krátká (životnost kanálu).

## <a name="message-formatting-and-messaging-activities"></a>Formátování zpráv a aktivity zasílání zpráv

<xref:System.ServiceModel.Activities.Receive>Aktivity a <xref:System.ServiceModel.Activities.ReceiveReply> obsahují vlastnost s názvem `Content` . Tato vlastnost je typu <xref:System.ServiceModel.Activities.ReceiveContent> a představuje data, která <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.ReceiveReply> přijímá aktivita nebo aktivita. .NET Framework definuje dvě související třídy s názvem <xref:System.ServiceModel.Activities.ReceiveMessageContent> a <xref:System.ServiceModel.Activities.ReceiveParametersContent> obě, které jsou odvozeny z <xref:System.ServiceModel.Activities.ReceiveContent> . Nastavte <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.ReceiveReply> vlastnost aktivity nebo na `Content` instanci jednoho z těchto typů pro příjem dat do služby pracovního postupu. Typ, který se má použít, závisí na typu dat, které aktivita přijímá. Pokud aktivita obdrží `Message` objekt nebo typ kontraktu zprávy, použijte <xref:System.ServiceModel.Activities.ReceiveMessageContent> . Pokud aktivita obdrží sadu kontraktů dat nebo typů XML, které mohou být serializovány, použijte <xref:System.ServiceModel.Activities.ReceiveParametersContent> . <xref:System.ServiceModel.Activities.ReceiveParametersContent>umožňuje odeslat více parametrů, zatímco <xref:System.ServiceModel.Activities.ReceiveMessageContent> umožňuje pouze odeslání jednoho objektu, zprávy (nebo typu kontraktu zprávy).

> [!NOTE]
> <xref:System.ServiceModel.Activities.ReceiveMessageContent>lze také použít s jedním kontraktem dat nebo typem XML, který lze serializovat. Rozdíl mezi použitím <xref:System.ServiceModel.Activities.ReceiveParametersContent> s jediným parametrem a objektem předaným přímo do <xref:System.ServiceModel.Activities.ReceiveMessageContent> je formát drátového formátu. Obsah parametru je zabalen v elementu XML, který odpovídá názvu operace a serializovaný objekt je zabalen v elementu XML pomocí názvu parametru (například `<Echo><msg>Hello, World</msg></Echo>` ). Obsah zprávy není zabalen názvem operace. Místo toho je serializovaný objekt umístěn v rámci elementu XML pomocí názvu typu kvalifikovaného pro XML (například `<string>Hello, World</string>` ).

<xref:System.ServiceModel.Activities.Send>Aktivity a <xref:System.ServiceModel.Activities.SendReply> obsahují také vlastnost s názvem `Content` . Tato vlastnost je typu <xref:System.ServiceModel.Activities.SendContent> a představuje data, která <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> odesílá nebo aktivita. .NET Framework definuje dva související typy s názvem <xref:System.ServiceModel.Activities.SendMessageContent> a <xref:System.ServiceModel.Activities.SendParametersContent> obě odvozené z <xref:System.ServiceModel.Activities.SendContent> . Nastavte <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> vlastnost aktivity nebo na `Content` instanci jednoho z těchto typů pro odesílání dat ze služby pracovního postupu. Typ, který se má použít, závisí na typu dat, které aktivita odesílá. Pokud aktivita odešle `Message` objekt nebo typ kontraktu zprávy, použijte <xref:System.ServiceModel.Activities.SendMessageContent> . Pokud aktivita odešle typ kontraktu dat, použijte <xref:System.ServiceModel.Activities.SendParametersContent> . <xref:System.ServiceModel.Activities.SendParametersContent>umožňuje odeslat více parametrů, zatímco <xref:System.ServiceModel.Activities.SendMessageContent> umožňuje pouze odeslat jeden objekt, zprávu (nebo typ kontraktu zprávy).

V případě imperativního programování pomocí aktivit zasílání zpráv, použijte obecné <xref:System.Activities.InArgument%601> a <xref:System.Activities.OutArgument%601> k zabalení objektů, které přiřadíte ke zprávě nebo parametrům <xref:System.ServiceModel.Activities.Send> pro <xref:System.ServiceModel.Activities.SendReply> aktivity,, <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.ReceiveReply> . Použijte <xref:System.Activities.InArgument%601> pro <xref:System.ServiceModel.Activities.Send> aktivity a a <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.OutArgument%601> pro aktivity a <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.ReceiveReply> . `In`argumenty se používají u aktivit odeslání, protože data se předávají do aktivit. `Out`argumenty se používají s aktivitami Receive, protože data se předávají mimo aktivity, jak je znázorněno v následujícím příkladu.

```csharp
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

Při implementaci služby pracovního postupu, která definuje operaci požadavku a odpovědi, která vrací typ void, je nutné vytvořit instanci <xref:System.ServiceModel.Activities.SendReply> aktivity a nastavit <xref:System.ServiceModel.Activities.SendReply.Content%2A> vlastnost na prázdnou instanci jednoho z typů obsahu ( <xref:System.ServiceModel.Activities.SendMessageContent> nebo <xref:System.ServiceModel.Activities.SendParametersContent> ), jak je znázorněno v následujícím příkladu.

```csharp
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

## <a name="add-service-reference"></a>Přidat odkaz na službu

Při volání služby pracovního postupu z aplikace pracovního postupu aplikace Visual Studio 2012 generuje vlastní aktivity zasílání zpráv, které zapouzdřují obvyklé <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity používané v MEP požadavků a odpovědí. Chcete-li použít tuto funkci, klikněte pravým tlačítkem myši na projekt klienta v aplikaci Visual Studio a vyberte možnost **Přidat**  >  **odkaz na službu**. Do pole Adresa zadejte základní adresu služby a klikněte na Přejít. Dostupné služby se zobrazí v poli **služby:** . Rozbalte uzel Služba, aby se zobrazily podporované smlouvy. Vyberte kontrakt, který chcete volat, a v poli **operace** se zobrazí seznam dostupných operací. Pak můžete zadat obor názvů pro generovanou aktivitu a kliknout na tlačítko **OK**. Pak se zobrazí dialogové okno s oznámením, že operace byla úspěšně dokončena a že generované vlastní aktivity jsou v sadě nástrojů po opětovném sestavení projektu. Pro každou operaci definovanou v kontraktu služby existuje jedna aktivita. Po sestavení projektu můžete přetáhnout vlastní aktivity do pracovního postupu a nastavit všechny požadované vlastnosti v okně Vlastnosti.

## <a name="messaging-activity-templates"></a>Šablony aktivity zasílání zpráv

Aby bylo možné nastavit MEP požadavků a odpovědí na snazšího klienta a službu, Visual Studio 2012 poskytuje dvě šablony aktivity zasílání zpráv. `System.ServiceModel.Activities.Design.ReceiveAndSendReply`se používá ve službě a `System.ServiceModel.Activities.Design.SendAndReceiveReply` používá se na klientovi. V obou případech šablony přidávají příslušné aktivity zasílání zpráv do pracovního postupu. Ve službě `System.ServiceModel.Activities.Design.ReceiveAndSendReply` přidá <xref:System.ServiceModel.Activities.Receive> aktivitu následovanou <xref:System.ServiceModel.Activities.SendReply> aktivitou. <xref:System.ServiceModel.Activities.SendReply.Request>Vlastnost je automaticky nastavena na <xref:System.ServiceModel.Activities.Receive> aktivitu. Na straně klienta `System.ServiceModel.Activities.Design.SendAndReceiveReply` přidá <xref:System.ServiceModel.Activities.Send> aktivitu, za kterou následuje <xref:System.ServiceModel.Activities.ReceiveReply> . <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>Vlastnost je automaticky nastavena na <xref:System.ServiceModel.Activities.Send> aktivitu. Chcete-li použít tyto šablony, stačí přetáhnout příslušnou šablonu do pracovního postupu.

## <a name="messaging-activities-and-transactions"></a>Aktivity zasílání zpráv a transakce

Když se ve službě pracovního postupu provede volání služby, může být vhodné přesměrovat transakci na operaci služby. Pokud to chcete udělat, umístěte <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. <xref:System.ServiceModel.Activities.TransactedReceiveScope>Aktivita obsahuje `Receive` aktivitu a tělo. Transakce, která se do služby Flowe, zůstává v průběhu provádění těla <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Transakce je dokončena, jakmile bude dokončeno vykonání těla. Další informace o pracovních postupech a transakcích najdete v tématu [transakce pracovního postupu](../../windows-workflow-foundation/workflow-transactions.md).

## <a name="see-also"></a>Viz také

- [Jak odesílat a přijímat chyby ve službách pracovních postupů](https://go.microsoft.com/fwlink/?LinkId=189151)
- [Vytvoření dlouhodobé služby pracovního postupu](creating-a-long-running-workflow-service.md)
