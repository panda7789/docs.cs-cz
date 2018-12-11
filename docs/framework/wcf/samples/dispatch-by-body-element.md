---
title: Přiřazování zpráv metodám podle elementu těla
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 58d505770a495e5e423104b9fb912d088ca56f86
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143152"
---
# <a name="dispatch-by-body-element"></a>Přiřazování zpráv metodám podle elementu těla
Tento příklad ukazuje, jak implementovat alternativní algoritmus pro přiřazení k operacím příchozí zprávy.  
  
 Ve výchozím nastavení, vybere dispečer modelu služby příslušné zpracování metody pro příchozí zprávy podle zprávy WS-Addressing "Action" záhlaví nebo ekvivalentní informace v požadavku SOAP protokolu HTTP.  
  
 Některé SOAP 1.1 webových služeb balíčky, které se neřídí WS-I Basic Profile 1.1 pokyny není odeslání zprávy založené na identifikátor URI akce, ale spíše založené na XML kvalifikovaný název prvního prvku uvnitř těla protokolu SOAP. Tyto balíčky na straně klienta, může odesílat zprávy pomocí prázdný nebo libovolné záhlaví HTTP SoapAction, které bylo povoleno ve specifikaci protokolu SOAP 1.1.  
  
 Chcete-li změnit způsob, jakým jsou zprávy odesílány metodám, ukázka implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozšiřitelnost rozhraní `DispatchByBodyElementOperationSelector`. Tato třída vybere operace založené na první prvek těla zprávy.  
  
 Konstruktor třídy očekává, že vyplní dvojice slovník `XmlQualifiedName` a řetězce, kterým kvalifikované názvy odděluje název prvního podřízeného těla protokolu SOAP a řetězce označují odpovídající název operace. `defaultOperationName` Je název operace, která přijímá všechny zprávy, které nejde spárovat proti tomuto slovníku:  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementace jsou velmi jednoduché k sestavení, protože existuje jenom jedna metoda v rozhraní: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>. Úloha této metody je ke kontrole příchozích zpráv a vrátí řetězec, který se rovná název metody u kontraktu služby pro aktuální koncový bod.  
  
 V tomto příkladu získá selektor operace <xref:System.Xml.XmlDictionaryReader> pro příchozí zprávy textu v nástrojích <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Tato metoda čtecí modul již umístí na prvním podřízeným těla zprávy tak, aby je dostatečné pro získání názvu a oboru názvů identifikátoru URI aktuálního elementu a zkombinujte je do `XmlQualifiedName` , která se pak použije pro vyhledávání odpovídající operace slovník drží selektor operace.  
  
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
  
 Přístup k textu zprávy s <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> nebo některou z metod, které poskytují přístup k obsahu těla zprávy způsobí, že zpráva, která má být označený jako "čtení", což znamená, že zpráva není platná pro další zpracování. Selektor operace proto vytvoří kopii příchozí zprávy s metodou je znázorněno v následujícím kódu. Protože při kontrole nedošlo ke změně pozice čtenáře, lze odkazovat pomocí nově vytvořeného zpráv ke kterému vlastnosti zprávy a záhlaví zpráv jsou zkopírovány také, což vede k přesné klon původní zprávy:  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a>Přidání selektor operace služby  
 Selektory operaci odeslání služby jsou rozšíření pro dispečera Windows Communication Foundation (WCF). Pro výběr metody zpětného volání kanál duplexní kontrakty, existují také selektory provozu klienta, které fungují velmi podobně jako selektory operaci odeslání je zde popsáno, ale která nejsou výslovně uvedena v této ukázce.  
  
 Jako většina rozšíření modelů služeb se přidají selektory operaci odeslání do dispečera pomocí chování. A *chování* je objekt konfigurace, která přidá jeden nebo více rozšíření modulu runtime odeslání (nebo modul runtime klienta) nebo v opačném případě se změní jeho nastavení.  
  
 Vzhledem k tomu, že selektory operace kontraktu oboru, je odpovídající chování k implementaci tady <xref:System.ServiceModel.Description.IContractBehavior>. Protože rozhraní je implementováno v <xref:System.Attribute> odvozené třídy jak je znázorněno v následujícím kódu, chování lze deklarativně přidat do jakékoli kontrakt služby. Pokaždé, když se <xref:System.ServiceModel.ServiceHost> je otevřený a sestaven modul runtime odeslání, najít všechny chování jako atributy u kontraktů, operace a implementací služby nebo jako prvek v konfiguraci služby se automaticky přidá a následně vyzve k přispívat rozšíření nebo změnit výchozí konfiguraci.  
  
 Pro zkrácení, následující úryvek kódu se zobrazují jenom implementaci metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, což ovlivňuje změny konfigurace pro dispečera v této ukázce. Jiné metody se nezobrazují, vzhledem k tomu, aniž by každé dílo vrácení volajícímu.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Nejprve je potřeba <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementace vyhledávacího slovníku za selektor operace nastaví pomocí provádí iterace <xref:System.ServiceModel.Description.OperationDescription> prvky v koncovém bodě služby <xref:System.ServiceModel.Description.ContractDescription>. Potom se každý popis operace prozkoumá přítomnost `DispatchBodyElementAttribute` chování, implementace <xref:System.ServiceModel.Description.IOperationBehavior> , který je také definováno v této ukázce. Tato třída je také chování, je pasivní činnost a není aktivně přispět změny konfigurace modulu runtime odeslání. Všechny jeho metody vracet volajícímu bez jakékoli akce. Chování operace existuje pouze tak, aby byla metadata potřebná pro nové odeslání mechanismus, konkrétně kvalifikovaný název prvku textu na jehož výskyt operace zaškrtnuto, mohou být spojeny s příslušné operace.  
  
 Pokud takové chování není nalezen, hodnota pár vytvořené z XML kvalifikovaný název (`QName` vlastnost) a název operace (`Name` vlastnost) se přidá do slovníku.  
  
 Po naplnění slovníku nový `DispatchByBodyElementOperationSelector` je vytvořen pomocí těchto informací a nastavit jako selektor operace odeslání Runtime:  
  
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
  
## <a name="implementing-the-service"></a>Implementace této služby  
 Chování, které jsou implementovány v této ukázce přímo ovlivní jak přenosu interpretován a zpráv odeslaných, což je funkce kontraktu služby. V důsledku toho by měly být deklarovány chování na úrovni kontraktu služby v jakékoli implementaci služby, který vybírá jeho použití.  
  
 Služba projektu vzorku se vztahuje `DispatchByBodyElementBehaviorAttribute` smlouvy chování `IDispatchedByBody` smlouvy a popisky z těchto dvou operací služby `OperationForBodyA()` a `OperationForBodyB()` s `DispatchBodyElementAttribute` chování operace. Při otevření hostitele služby pro službu, která implementuje tento kontrakt tato metadata je převzata tvůrcem dispečer jak bylo popsáno dříve.  
  
 Protože modulu pro výběr operace odešle výhradně podle elementu těla zprávy a ignoruje "Action", je potřeba zjistit, modul runtime není ke kontrole "Action" záhlaví odpovědi vrácené přiřazením zástupný znak "*" na `ReplyAction` vlastnost <xref:System.ServiceModel.OperationContractAttribute>. Kromě toho je potřeba mít výchozí operaci, která má vlastnost "Action" nastavenou na zástupný znak "\*". Výchozí operaci přijímá všechny zprávy, které se nedají odbavovat a nemá `DispatchBodyElementAttribute`:  
  
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
  
 Ukázková implementace služby je jednoduché. EVERY – metoda zabalí do zprávy s odpovědí přijatou zprávu a vrátí ji zpět do klienta.  
  
## <a name="running-and-building-the-sample"></a>Spuštění a sestavování vzorku  
 Při spuštění ukázky obsah textu odpovědi operace se zobrazují v okně konzoly klienta, podobně jako následující výstup (formátovaný).  
  
 Klient odešle tři zprávy do služby jehož obsahu je s názvem elementu těla `bodyA`, `bodyB`, a `bodyX`v uvedeném pořadí. Jako může být odložena z předchozí popis a kontrakt služby uvedené, příchozí zprávy s `bodyA` element je odeslána `OperationForBodyA()` metoda. Protože neexistuje žádný explicitní odeslání cíl pro zprávu s `bodyX` body element, je odeslána zpráva `DefaultOperation()`. Každá z operací služby zalomí text zprávy přijaté do elementu specifické pro metodu a vrátí jej, která se provádí korelaci vstupní a výstupní zprávy jasně pro tuto ukázku:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a>Viz také
