---
title: Přiřazování zpráv metodám podle elementu těla
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 754151f856dfe09b8fd12912ab06d1d8720be016
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183714"
---
# <a name="dispatch-by-body-element"></a>Přiřazování zpráv metodám podle elementu těla
Tato ukázka ukazuje, jak implementovat alternativní algoritmus pro přiřazování příchozích zpráv k operacím.  
  
 Ve výchozím nastavení dispečer modelu služby vybere vhodnou metodu zpracování pro příchozí zprávu na základě hlavičky "Akce" adresování WS zprávy nebo ekvivalentních informací v požadavku HTTP SOAP.  
  
 Některé zásobníky webových služeb SOAP 1.1, které nedodržují pokyny WS-I Basic Profile 1.1, neodesílají zprávy založené na identifikátoru URI akce, ale spíše na základě kvalifikovaného názvu jazyka XML prvního prvku uvnitř těla SOAP. Podobně straně klienta těchto zásobníků může odesílat zprávy s prázdnou nebo libovolnou hlavičkou HTTP SoapAction, která byla povolena specifikací SOAP 1.1.  
  
 Chcete-li změnit způsob, jakým jsou odesílány <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> zprávy metod, ukázka implementuje rozhraní rozšiřitelnosti `DispatchByBodyElementOperationSelector`na rozhraní . Tato třída vybere operace na základě prvního prvku textu zprávy.  
  
 Konstruktor třídy očekává slovník naplněný dvojicemi `XmlQualifiedName` a řetězce, přičemž kvalifikované názvy označují název prvního podřízeného těla SOAP a řetězce označují odpovídající název operace. Název `defaultOperationName` operace, která přijímá všechny zprávy, které nelze porovnat s tímto slovníkem:  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementace jsou velmi jednoduché stavět, protože existuje pouze <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>jedna metoda na rozhraní: . Úlohou této metody je zkontrolovat příchozí zprávu a vrátit řetězec, který se rovná názvu metody na servisní smlouvě pro aktuální koncový bod.  
  
 V této ukázce volič <xref:System.Xml.XmlDictionaryReader> operace získá pro text příchozí <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>zprávy pomocí . Tato metoda již umístí čtenáře na první podřízené tělo zprávy tak, aby bylo dostačující získat název aktuálního prvku a identifikátor URI oboru názvů a kombinovat je `XmlQualifiedName` do, který se pak používá pro vyhledání odpovídající operace ze slovníku drženého volič operace.  
  
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
  
 Přístup k textu <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> zprávy s nebo některou z dalších metod, které poskytují přístup k obsahu textu zprávy způsobí, že zpráva bude označena jako "číst", což znamená, že zpráva je neplatná pro jakékoli další zpracování. Proto selekto operace vytvoří kopii příchozí zprávy s metodou uvedenou v následujícím kódu. Vzhledem k tomu, že pozice čtenáře nebyla během kontroly změněna, může být odkazována nově vytvořenou zprávou, do které jsou také zkopírovány vlastnosti zprávy a záhlaví zprávy, což má za následek přesný klon původní zprávy:  
  
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
 Selektory operací odeslání služby jsou rozšíření dispečera WCF (Windows Communication Foundation). Pro výběr metod na kanálu zpětného volání duplexních smluv existují také voliči operací klienta, které fungují velmi podobně jako voliči operace odeslání popsané zde, ale které nejsou explicitně zahrnuty v této ukázce.  
  
 Stejně jako většina rozšíření modelu služby, selektory operace odeslání jsou přidány do dispečera pomocí chování. *Chování* je konfigurační objekt, který přidá jedno nebo více rozšíření do časového času odeslání (nebo do klientského runtime) nebo jinak změní jeho nastavení.  
  
 Vzhledem k tomu, že selektory operací mají <xref:System.ServiceModel.Description.IContractBehavior>rozsah smlouvy, vhodné chování k implementaci zde je . Vzhledem k tomu, <xref:System.Attribute> že rozhraní je implementováno na odvozené třídy, jak je znázorněno v následujícím kódu, chování může být deklarativně přidándo jakékoli smlouvy o poskytování služeb. <xref:System.ServiceModel.ServiceHost> Při každém otevření a spuštění runtime odeslání jsou všechna chování nalezena buď jako atributy na smlouvy, operace a implementace služby nebo jako prvek v konfiguraci služby jsou automaticky přidány a následně požádáni, aby přispěly rozšíření nebo upravit výchozí konfiguraci.  
  
 Pro stručnost následující kód výňatek zobrazuje pouze implementaci <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>metody , která má vliv na změny konfigurace pro dispečera v této ukázce. Ostatní metody nejsou zobrazeny, protože se vrátí volajícímu bez provedení jakékoli práce.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Nejprve <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementace nastaví vyhledávací slovník pro volič operací iteracepřes <xref:System.ServiceModel.Description.OperationDescription> prvky v <xref:System.ServiceModel.Description.ContractDescription>koncovém bodě služby . Potom každý popis operace je zkontrolovánna `DispatchBodyElementAttribute` přítomnost chování, <xref:System.ServiceModel.Description.IOperationBehavior> implementace, která je také definována v této ukázce. Zatímco tato třída je také chování, je pasivní a nepřispívá aktivně žádné změny konfigurace spuštění odeslání. Všechny jeho metody vrátit volajícímu bez nutnosti jakékoli akce. Chování operace existuje pouze proto, aby metadata požadovaná pro nový mechanismus odeslání, konkrétně kvalifikovaný název prvku těla, na jehož výskytu je operace vybrána, mohou být přidružena k příslušným operacím.  
  
 Pokud je takové chování nalezeno, je do slovníku`QName` přidán pár hodnot`Name` vytvořený z kvalifikovaného názvu XML (vlastnost) a název operace ( vlastnost).  
  
 Po naplnění slovníku je `DispatchByBodyElementOperationSelector` vytvořen nový s těmito informacemi a nastaven jako volič operace dispečera runtime:  
  
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
 Chování implementované v této ukázce přímo ovlivňuje způsob interpretace a odeslání zpráv z drátu, což je funkce smlouvy o poskytování služeb. V důsledku toho by mělo být chování deklarováno na úrovni servisní smlouvy v jakékoli implementaci služby, která se rozhodne ji použít.  
  
 Ukázková projektová služba `DispatchByBodyElementBehaviorAttribute` použije chování `IDispatchedByBody` smlouvy na servisní smlouvu `OperationForBodyA()` `OperationForBodyB()` a `DispatchBodyElementAttribute` označí každou ze dvou operací a chování operace. Při otevření hostitele služby pro službu, která implementuje tuto smlouvu, tato metadata je vyzvednuta tvůrcem dispečera, jak bylo popsáno dříve.  
  
 Vzhledem k tomu, že se volič operace odesílá výhradně na základě elementu textu zprávy a ignoruje "Akce", je nutné sdělit, aby ovládací prvek `ReplyAction` runtime <xref:System.ServiceModel.OperationContractAttribute>nekontroloval záhlaví "Akce" na vrácených odpovědích přiřazením zástupného znaku "*" vlastnosti . Kromě toho je nutné mít výchozí operaci, která má vlastnost "Akce"\*nastavena na zástupný znak " ". Výchozí operace přijímá všechny zprávy, které nelze odeslat `DispatchBodyElementAttribute`a nemá :  
  
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
  
 Ukázková implementace služby je jednoduchá. Každá metoda zalomí přijatou zprávu do zprávy s odpovědí a vrátí ji zpět klientovi.  
  
## <a name="running-and-building-the-sample"></a>Běh a vytváření ukázky  
 Při spuštění ukázky, obsah těla operace odpovědi jsou zobrazeny v okně klientské konzole podobné následující (formátovaný) výstup.  
  
 Klient odešle službě tři zprávy, jejichž `bodyA`element `bodyB`obsahu `bodyX`těla je pojmenován , a , v uvedeném pořadí. Jak může být odloženo z předchozího popisu a zobrazené `bodyA` servisní smlouvy, příchozí `OperationForBodyA()` zpráva s elementem je odeslána do metody. Vzhledem k tomu, že neexistuje `bodyX` žádný cíl explicitní odeslání zprávy `DefaultOperation()`s elementem body, je zpráva odeslána do . Každá operace služby zabalí text přijaté zprávy do prvku specifického pro metodu a vrátí jej, což se provádí korelovat vstupní a výstupní zprávy jasně pro tuto ukázku:  
  
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
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
