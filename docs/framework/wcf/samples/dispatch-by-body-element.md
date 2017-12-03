---
title: "Přiřazování zpráv metodám podle elementu těla"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c3624290176d93519ae420a98a7e93534d910fa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="dispatch-by-body-element"></a>Přiřazování zpráv metodám podle elementu těla
Tento příklad znázorňuje způsob implementace alternativní algoritmus pro přiřazení k operacím příchozí zprávy.  
  
 Ve výchozím nastavení vybere dispečera modelu služby příslušné zpracování metodu pro příchozí zprávy založené na protokolu WS-Addressing zprávy "Action" záhlaví nebo ekvivalentní informace v požadavku HTTP SOAP.  
  
 Některé SOAP 1.1 webových služeb zásobníky, které neodpovídají WS-I Basic Profile 1.1 pokyny není odesílání zpráv na základě v identifikátoru URI akce, ale spíš podle XML kvalifikovaný název první prvek uvnitř těla protokolu SOAP. Tyto balíčky na straně klienta, může odesílat zprávy s prázdná nebo libovolný HTTP SoapAction hlavičky, která byla povolena specifikací SOAP 1.1.  
  
 Chcete-li změnit způsob, jakým se odesílají zprávy do metod, implementuje vzorku <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozšiřitelnost rozhraní na `DispatchByBodyElementOperationSelector`. Tato třída vybere operace založené na první prvek textu zprávy.  
  
 Konstruktoru třídy očekává slovník naplněný dvojici `XmlQualifiedName` a řetězce, kterým kvalifikované názvy označení názvu prvního podřízeného těla protokolu SOAP a řetězce znamenat odpovídající název operace. `defaultOperationName` Je název operace, která přijímá všechny zprávy, které nelze porovnání tohoto slovníku:  
  
```  
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementace jsou velmi jednoduché, jako je pouze jednu metodu na rozhraní pro sestavení: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>. Úloha tato metoda je kontrola příchozí zprávy a vrátí řetězec, který se rovná názvu metody na kontrakt služby pro aktuální koncový bod.  
  
 V této ukázce získá selektor operace <xref:System.Xml.XmlDictionaryReader> pro příchozí zprávy je text použití <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Tato metoda již umisťuje čtečky na prvním podřízeným objektem těla zprávy, tak, aby se pro získání aktuálního elementu název a identifikátor URI oboru názvů a zkombinovat do dostatečná `XmlQualifiedName` , pak se používá pro vyhledávání odpovídající operaci provést z slovník držené selektor operace.  
  
```  
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
  
 Přístup k tělo zprávy s <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> nebo některou z metod, které poskytují přístup k obsahu tělo zprávy způsobí, že zpráva byla označena jako "číst", což znamená, že zprávy je neplatný pro další zpracování. Proto selektor operace vytvoří kopii příchozí zprávy s metodou vidět v následujícím kódu. Protože pozice čtenáře nebylo změněno při kontrole, může být odkazován nově vytvořenou zprávu do které vlastnosti zprávy a záhlaví zprávy jsou také zkopírovali, což vede přesný klon na původní zprávu o:  
  
```  
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
 Selektory operace odesílání služby jsou rozšíření pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dispečera. Pro výběr metody zpětného volání kanál duplexní kontrakty, existují také selektory operace klienta, které fungují velmi podobně, jako jsou zde popsané selektory operace odesílání, ale které nejsou výslovně zahrnuty v této ukázce.  
  
 Jako většina rozšíření model služeb jsou selektory operace odesílání přidány do dispečera pomocí chování. A *chování* je objekt konfigurace, která přidá jeden nebo více rozšíření odesílání runtime (nebo modul runtime klienta) nebo v opačném případě se změní jeho nastavení.  
  
 Vzhledem k tomu, že selektory operace oboru kontrakt, příslušné chování k implementaci tady je <xref:System.ServiceModel.Description.IContractBehavior>. Protože rozhraní je implementováno na <xref:System.Attribute> odvozené třídy jak je znázorněno v následujícím kódu, chování deklarativně přidáním jakékoli servisní smlouvou. Vždy, když <xref:System.ServiceModel.ServiceHost> je otevřen a odesílání runtime vychází, všechny chování nalezena jako atributy na smlouvy, operace a implementací služby nebo jako element v konfiguraci služby se automaticky přidá a následně se zobrazí výzva k přispívat rozšíření nebo změnit výchozí konfiguraci.  
  
 Jako stručný výtah následující výpis kódu se zobrazí pouze implementace metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, který ovlivňuje změny konfigurace pro dispečera v této ukázce. Jiné metody nezobrazují, protože vracejí volajícímu bez jakékoli pracuje.  
  
```  
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Nejdřív <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementace nastaví slovník vyhledávání pro selektor operace podle iterování přes <xref:System.ServiceModel.Description.OperationDescription> elementů v koncový bod služby <xref:System.ServiceModel.Description.ContractDescription>. Potom se každý popis operace prozkoumá přítomnost `DispatchBodyElementAttribute` chování, provádění <xref:System.ServiceModel.Description.IOperationBehavior> , je také definován v této ukázce. Když je tato třída také chování, je pasivní a není aktivně přispívat změny konfigurace modulu runtime odesílání. Všechny její metody vrátí volajícímu bez nutnosti převádět všechny akce. Operace chování existuje pouze tak, aby byla metadata potřebná pro nové odesílání mechanismus, konkrétně kvalifikovaný název prvku body na jejichž výskyt operace je vybrána, může být spojen s příslušnými operacemi.  
  
 Pokud je nalezen takové chování, dvojici hodnota vytvořené z XML úplný název (`QName` vlastnosti) a název operace (`Name` vlastnost) se přidá do slovníku.  
  
 Po zaplnění slovníku, a nové `DispatchByBodyElementOperationSelector` je vytvořená pomocí těchto informací a nastavena jako selektor operace odesílání modulu runtime:  
  
```  
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
 Chování implementována v této ukázce přímo ovlivňuje jak přenosu interpretovat a zpráv odeslaných, což je funkce kontrakt služby. Chování v důsledku toho musí deklarovat na úrovni kontraktu služby v implementaci žádné služby, který se tedy rozhodne použít ho.  
  
 Službu ukázkový projekt se vztahuje `DispatchByBodyElementBehaviorAttribute` smlouvy chování `IDispatchedByBody` služby kontrakt a štítky z těchto dvou operací `OperationForBodyA()` a `OperationForBodyB()` s `DispatchBodyElementAttribute` operaci chování. Po otevření hostitele služby pro službu, která implementuje tento kontrakt tato metadata převzata Tvůrce dispečera jak bylo popsáno dříve.  
  
 Protože selektor operace odešle zprávu výhradně podle elementu těla zprávy a ignoruje "Action", je třeba, aby říct modul runtime není zkontroluje hlavičky "Action" na vrácený odpovědi přiřazením zástupný znak "*" k `ReplyAction` vlastnost <xref:System.ServiceModel.OperationContractAttribute>. Kromě toho je potřeba mít výchozí operaci, která má vlastnost "Action" nastavená na zástupný znak "\*". Výchozí operaci přijímá všechny zprávy, které nelze odeslat a nemá `DispatchBodyElementAttribute`:  
  
```  
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
  
 Implementace služby ukázka je jednoduchá. EVERY – metoda zabalí přijatou zprávu do zprávu odpovědi a vrátí ji zpět do klienta.  
  
## <a name="running-and-building-the-sample"></a>Spuštění a sestavování vzorku  
 Při spuštění vzorového obsah textu odpovědi operace se zobrazují v okně konzoly klienta podobné výstupu v následujícím (formátovaný).  
  
 Klient odešle tři zprávy do služby jehož obsahu je s názvem elementu těla `bodyA`, `bodyB`, a `bodyX`, v uvedeném pořadí. Jak může být odložen z předchozí popis a kontrakt služby zobrazí, příchozích zpráv s `bodyA` element odeslaných `OperationForBodyA()` metoda. Vzhledem k tomu, že neexistuje žádné explicitní odesílání cíl pro zprávu s `bodyX` body element je zpráva odeslána na `DefaultOperation()`. Každý operací služby zabalí obsah přijaté zprávy do elementu specifické pro metodu a vrátí, která se provádí korelaci vstup a výstup zprávy jasně pro tuto ukázku:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a>Viz také
