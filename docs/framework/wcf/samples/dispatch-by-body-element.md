---
title: Přiřazování zpráv metodám podle elementu těla
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 19913cdaa47d766f62a313e216a653ac69633a99
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594696"
---
# <a name="dispatch-by-body-element"></a>Přiřazování zpráv metodám podle elementu těla
Tato ukázka předvádí, jak implementovat alternativní algoritmus pro přiřazování příchozích zpráv do operací.  
  
 Ve výchozím nastavení vybírá dispečer Service Model vhodnou metodu zpracování pro příchozí zprávu na základě hlavičky akce WS-Addressing zprávy nebo ekvivalentní informace v žádosti HTTP SOAP.  
  
 Některé zásobníky webových služeb SOAP 1,1, které nedodržují pokyny pro základní 1,1 Profil WS-I, neodesílají zprávy na základě identifikátoru URI akce, ale na základě XML kvalifikovaného názvu prvního prvku uvnitř těla protokolu SOAP. Podobně může Klientská strana těchto zásobníků odesílat zprávy s prázdnou hlavičkou HTTP SoapAction, která byla povolena specifikací protokolu SOAP 1,1.  
  
 Chcete-li změnit způsob, jakým jsou odesílány zprávy do metod, ukázka implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozhraní rozšiřitelnosti na `DispatchByBodyElementOperationSelector` . Tato třída vybere operace na základě prvního prvku textu zprávy.  
  
 Konstruktor třídy očekává slovník naplněný páry `XmlQualifiedName` a řetězce, přičemž kvalifikované názvy označují název prvního podřízeného textu protokolu SOAP a řetězce indikují název vyhovující operace. `defaultOperationName`Je název operace, která přijímá všechny zprávy, které nelze spárovat s tímto slovníkem:  
  
```csharp
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
}
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementace jsou velmi jednoduché k sestavení, protože rozhraní obsahuje pouze jednu metodu: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> . Úkolem této metody je zkontrolovat příchozí zprávu a vrátit řetězec, který se rovná názvu metody kontraktu služby pro aktuální koncový bod.  
  
 V této ukázce selektor operace získá <xref:System.Xml.XmlDictionaryReader> text pro tělo příchozí zprávy pomocí <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> . Tato metoda již umisťuje čtecí modul na první podřízený text zprávy tak, aby bylo možné získat název aktuálního prvku a identifikátor URI oboru názvů a zkombinovat je do objektu `XmlQualifiedName` , který je pak použit pro vyhledání odpovídající operace ze slovníku uloženého selektor operace.  
  
```csharp
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 Přístup k tělo zprávy pomocí <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> nebo libovolné jiné metody, která poskytuje přístup k obsahu obsahu zprávy způsobí, že zpráva bude označena jako "přečtená", což znamená, že zpráva není pro jakékoli další zpracování platná. Proto selektor operací vytvoří kopii příchozí zprávy s metodou zobrazenou v následujícím kódu. Vzhledem k tomu, že se pozice čtecího zařízení během kontroly nezměnila, může být odkazováno nově vytvořenou zprávou, na kterou jsou také zkopírovány vlastnosti zprávy a záhlaví zpráv, což má za následek přesný klon původní zprávy:  
  
```csharp
private Message CreateMessageCopy(Message message,
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a>Přidání voliče operace do služby  
 Selektory operací odeslání služby jsou rozšířením dispečera Windows Communication Foundation (WCF). Pro výběr metod na kanálu zpětného volání u kontraktů s překrytím jsou k dispozici také selektory operací klienta, které fungují velmi podobně jako selektory operací odeslání popsané zde, ale nejsou výslovně popsány v této ukázce.  
  
 Podobně jako u většiny rozšíření modelu služeb jsou selektory operací odeslání přidány do dispečera pomocí chování. *Chování* je objekt konfigurace, který buď přidá jednu nebo více rozšíření do modulu runtime odeslání (nebo do modulu runtime klienta), nebo jinak změní jeho nastavení.  
  
 Vzhledem k tomu, že selektory operací mají obor kontraktu, příslušné chování, které se má implementovat, je <xref:System.ServiceModel.Description.IContractBehavior> . Protože rozhraní je implementováno pro <xref:System.Attribute> odvozenou třídu, jak je znázorněno v následujícím kódu, může být chování deklarativně přidáno do jakékoli kontraktu služby. Pokaždé <xref:System.ServiceModel.ServiceHost> , když se otevře a spustí se modul runtime Dispatch, všechna chování zjištěná buď jako atributy kontraktů, operací a implementací služby, nebo jako element v konfiguraci služby jsou automaticky přidány a následně vyzvány k rozšířením aplikace Contribute nebo úpravám výchozí konfigurace.  
  
 V případě zkrácení následující úryvek kódu zobrazuje pouze implementaci metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> , která ovlivňuje změny konfigurace dispečera v této ukázce. Jiné metody nejsou zobrazeny, protože se vrací volajícímu bez provedení jakékoli práce.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Nejprve <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementace nastaví slovník vyhledávání pro selektor operací tak, že provede iteraci <xref:System.ServiceModel.Description.OperationDescription> prvků v rámci koncového bodu služby <xref:System.ServiceModel.Description.ContractDescription> . Pak je u každého popisu operace prověřena přítomnost `DispatchBodyElementAttribute` chování, implementace <xref:System.ServiceModel.Description.IOperationBehavior> , která je také definována v této ukázce. I když je tato třída také chování, je pasivní a neaktivně nepřispívá ke změnám konfigurace modulu runtime odeslání. Všechny jeho metody se vrátí volajícímu bez provedení jakýchkoli akcí. Chování operace existuje pouze proto, že metadata požadovaná pro nový mechanismus odeslání, Jmenovitý název prvku tělo, u jehož výskytu operace je vybrána, lze přidružit k příslušným operacím.  
  
 Pokud je takové chování nalezeno, je do slovníku přidána dvojice hodnot vytvořená z kvalifikovaného názvu XML ( `QName` vlastnost) a název operace ( `Name` vlastnost).  
  
 Po naplnění slovníku se nový vytvoří `DispatchByBodyElementOperationSelector` s těmito informacemi a nastaví se jako selektor operace modulu runtime pro odesílání:  
  
```csharp
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a>Implementace služby  
 Chování implementované v této ukázce přímo ovlivňuje způsob interpretace a odeslání zpráv z tohoto drátu, což je funkce kontraktu služby. V důsledku toho by mělo být chování deklarováno na úrovni kontraktu služby v jakékoli implementaci služby, kterou se rozhodnete použít.  
  
 Ukázková služba projektu používá `DispatchByBodyElementBehaviorAttribute` chování kontraktu pro `IDispatchedByBody` kontrakt služby a popisky každé z těchto dvou operací `OperationForBodyA()` a `OperationForBodyB()` s `DispatchBodyElementAttribute` chováním operace. Po otevření hostitele služby pro službu, která implementuje tuto smlouvu, je tato metadata převzata tvůrcem dispečera, jak je popsáno výše.  
  
 Vzhledem k tomu, že se selektor operace odesílá výhradně na základě prvku těla zprávy a ignoruje "Action", je nutné sdělit modulu runtime, aby nekontroloval hlavičku "Action" na vrácených odpovědí přiřazením zástupného znaku "*" k `ReplyAction` vlastnosti <xref:System.ServiceModel.OperationContractAttribute> . Kromě toho je nutné mít výchozí operaci, která má vlastnost "Action" nastavenou na zástupný znak " \* ". Výchozí operace přijímá všechny zprávy, které nelze odeslat a nemá `DispatchBodyElementAttribute` :  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 Implementace ukázkové služby je jednoduchá. Každá metoda zabalí přijatou zprávu do zprávy s odpovědí a vrátí ji zpět klientovi.  
  
## <a name="running-and-building-the-sample"></a>Spuštění a sestavování ukázky  
 Když spustíte ukázku, v okně konzoly klienta se zobrazí obsah textu odpovědí operace, který bude podobný následujícímu (formátovanému) výstupu.  
  
 Klient pošle službě tři zprávy, jejichž tělo elementu obsahu se jmenuje `bodyA` , `bodyB` a v `bodyX` uvedeném pořadí. Jak je možné odvodit z předchozího popisu a uvedeného kontraktu služby, příchozí zpráva s `bodyA` prvkem je odeslána do `OperationForBodyA()` metody. Vzhledem k tomu, že není k dispozici žádný explicitní cíl odeslání zprávy s `bodyX` elementem body, zpráva je odeslána na `DefaultOperation()` . Každá operace služby zabalí přijatý text zprávy do prvku specifického pro metodu a vrátí jej, který je pro účely této ukázky možné jednoznačně sladit vstupní a výstupní zprávy:  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
