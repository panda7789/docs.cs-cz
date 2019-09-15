---
title: Interoperabilita s webovými službami ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 59ee6412cde152588e8007fe530cc8e5708410e5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991535"
---
# <a name="interoperability-with-aspnet-web-services"></a>Interoperabilita s webovými službami ASP.NET
Vzájemná spolupráce mezi webovými službami ASP.NET Web Services a Windows Communication Foundation (WCF) je možné dosáhnout tím, že zajistíte, aby služby implementované pomocí obou technologií splňovaly specifikaci 1,1 profilu WS-I Basic. Webové služby ASP.NET, které odpovídají profilu WS-I Basic Profile 1,1, se vzájemně spolupracují s klienty WCF pomocí vazby <xref:System.ServiceModel.BasicHttpBinding>poskytované systémem služby WCF.  
  
 Použijte možnost ASP.NET 2,0 pro přidání <xref:System.Web.Services.WebService> atributů a <xref:System.Web.Services.WebMethodAttribute> k rozhraní, nikoli ke třídě, a zápis třídy pro implementaci rozhraní, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 Použití této možnosti je preferované, protože rozhraní s <xref:System.Web.Services.WebService> atributem představuje kontrakt pro operace prováděné službou, které lze znovu použít s různými třídami, které mohou implementovat stejný kontrakt různými způsoby.  
  
 Nepoužívejte `SOAPAction` atribut ke směrování zpráv na metody založené na plně kvalifikovaném názvu prvku těla zprávy SOAP, nikoli v hlavičce protokolu HTTP. <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> WCF používá `SOAPAction` hlavičku protokolu HTTP pro zprávy směrování.  
  
 Kód XML, do <xref:System.Xml.Serialization.XmlSerializer> kterého je ve výchozím nastavení serializován typ, je sémanticky totožný s XML, do <xref:System.Runtime.Serialization.DataContractSerializer> kterého je serializován typ, za předpokladu, že obor názvů XML je explicitně definován. Při definování datového typu pro použití s ASP. NETWeb Services při předvídání přijímání služby WCF postupujte takto:  
  
- Definujte typ pomocí .NET Framework třídy místo schématu XML.  
  
- Přidejte pouze <xref:System.SerializableAttribute> třídu <xref:System.Xml.Serialization.XmlRootAttribute> a ke třídě pomocí druhé k explicitnímu definování oboru názvů pro daný typ. Nepřidávejte další atributy z <xref:System.Xml.Serialization> oboru názvů, abyste mohli určit, jak se má třída .NET Framework přeložit do XML.  
  
- Přijetím tohoto přístupu byste měli být schopni později převést třídy .NET na kontrakty dat s přidáním <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> bez významně měnit kód XML, do kterého jsou třídy serializovány pro přenos. Typy, které se používají ve zprávách pomocí webových služeb ASP.NET, je možné zpracovat jako kontrakty dat aplikacemi WCF, a to mimo jiné výhody a lepší výkon v aplikacích WCF.  
  
 Nepoužívejte možnosti ověřování poskytované Internetová informační služba (IIS). Klienti WCF je nepodporují. Pokud musí být služba zabezpečená, použijte možnosti poskytované službou WCF, protože tyto možnosti jsou robustní a jsou založené na standardních protokolech.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Dopad na výkon způsobený načtením modulu pro odeslání ServiceModel  
 V .NET Framework 3,0 byla služba WCF `HttpModule` nainstalována do kořenového souboru Web. config tak, aby každá aplikace ASP.NET byla povolená služba WCF. To může mít vliv na výkon, takže můžete `ServiceModel` soubor Web. config odebrat, jak je znázorněno v následujícím příkladu.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
