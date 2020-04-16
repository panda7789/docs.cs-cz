---
title: Interoperabilita s webovými službami ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 41810d8044e4b7ff3193950a914edbf1e61cffb1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464095"
---
# <a name="interoperability-with-aspnet-web-services"></a>Interoperabilita s webovými službami ASP.NET
Interoperability mezi ASP.NET webovými službami a webovými službami WCF (Windows Communication Foundation) lze dosáhnout zajištěním, aby služby implementované pomocí obou technologií odpovídaly specifikaci WS-I Basic Profile 1.1. ASP.NET webové služby, které odpovídají WS-I Základní profil 1.1 jsou interoperabilní s <xref:System.ServiceModel.BasicHttpBinding>wcf klienty pomocí WCF systémem poskytované vazby , .  
  
 Použijte ASP.NET možnost 2.0 <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> přidání atributy a do rozhraní spíše než do třídy a psaní třídy k implementaci rozhraní, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Použití této možnosti je upřednostňováno, protože rozhraní s atributem <xref:System.Web.Services.WebService> představuje kontrakt pro operace prováděné službou, které lze znovu použít s různými třídami, které mohou implementovat stejnou smlouvu různými způsoby.  
  
 Nepoužívejte <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut k tomu, aby zprávy byly směrovány na metody založené na plně `SOAPAction` kvalifikovaném názvu prvku body zprávy SOAP, nikoli na hlavičku HTTP. WCF používá `SOAPAction` hlavičku HTTP pro směrování zpráv.  
  
 Xml, do <xref:System.Xml.Serialization.XmlSerializer> kterého serializuje typ ve výchozím nastavení je sémanticky identické s XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializes typu, za předpokladu, že obor názvů pro XML je explicitně definován. Při definování datového typu pro použití se službami ASP.NETWeb v očekávání přijetí WCF postupujte takto:  
  
- Definujte typ pomocí tříd rozhraní .NET Framework, nikoli schématu XML.  
  
- Přidejte <xref:System.SerializableAttribute> pouze <xref:System.Xml.Serialization.XmlRootAttribute> a a do třídy, pomocí druhé explicitně definovat obor názvů pro typ. Nepřidávejte další atributy <xref:System.Xml.Serialization> z oboru názvů, abyste řídili, jak má být třída rozhraní .NET Framework přeložena do jazyka XML.  
  
- Přijetím tohoto přístupu byste měli být schopni později provést třídy .NET do datových kontraktů s přidáním <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> bez významné změny XML, do kterého jsou třídy serializovány pro přenos. Typy používané ve zprávách ASP.NET webových služeb mohou být zpracovány jako kontrakty dat aplikacemi WCF, což mimo jiné přináší lepší výkon v aplikacích WCF.  
  
 Nepoužívejte možnosti ověřování poskytované Internetovou informační službou (IIS). Klienti WCF je nepodporují. Pokud musí být služba zabezpečena, použijte možnosti poskytované WCF, protože tyto možnosti jsou robustní a jsou založeny na standardních protokolech.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Dopad na výkon způsobený načtením modulu ServiceModel HttpModule  
 V rozhraní .NET Framework 3.0 `HttpModule` byl wcf nainstalován v kořenovém souboru Web.config tak, aby každá ASP.NET aplikace byla povolena WCF. To může ovlivnit výkon, `ServiceModel` takže můžete odebrat soubor Web.config, jak je znázorněno v následujícím příkladu.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a>Viz také

- [Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
