---
title: Interoperabilita s webovými službami ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 3d4416a67d467f60fa381abc648c3a7ea0b9ada1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713322"
---
# <a name="interoperability-with-aspnet-web-services"></a>Interoperabilita s webovými službami ASP.NET
Vzájemná funkční spolupráce mezi [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webových služeb a služeb Windows Communication Foundation (WCF) Web můžete dosáhnout tím, že zajišťuje, že služby implementované pomocí obou technologií odpovídají WS-I Basic Profile 1.1 specifikace. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Webové služby, které odpovídají WS-I Basic Profile 1.1 se vzájemná spolupráce s klienty WCF pomocí WCF vazeb poskytovaných systémem, <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Použití [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] možnost Přidat <xref:System.Web.Services.WebService> a <xref:System.Web.Services.WebMethodAttribute> atributy rozhraní, nikoli třída a zápis třídu pro implementaci rozhraní, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
  
 Pomocí této možnosti je upřednostňované, protože rozhraní s <xref:System.Web.Services.WebService> atributu tvoří kontrakt operace prováděné na službu, kterou lze opětovně použít s různými třídami, které mohou implementovat tento stejný kontrakt různými způsoby.  
  
 Vyhněte se použití <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut zprávy směruje do metody podle plně kvalifikovaný název elementu těla zprávy protokolu SOAP místo `SOAPAction` hlavičky protokolu HTTP. Používá WCF `SOAPAction` hlavičku protokolu HTTP pro směrování zpráv.  
  
 XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky shodná s XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podle oboru názvů XML není výslovně uveden. Při definování datový typ pro použití s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]webové služby na případná přijetí WCF, postupujte takto:  
  
-   Definování typů pomocí tříd rozhraní .NET Framework než schématu XML.  
  
-   Přidat pouze <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.XmlRootAttribute> na třídu pomocí odkazující k explicitnímu definování oboru názvů typu. Nepřidávejte další atributy z <xref:System.Xml.Serialization> obor názvů řídit, jak je třída rozhraní .NET Framework mají být převedeny do jazyka XML.  
  
-   Přijetím tohoto přístupu by měl být schopen později provést třídy rozhraní .NET v kontraktech dat a uveďte <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> beze změny výrazně XML, do které třídy serializují pro přenos. Typy používané v zprávy podle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby může zpracovat jako kontraktů dat aplikací služby WCF, což má za následek, kromě dalších výhod, lepší výkon v aplikacích WCF.  
  
 Vyhněte se použití možnosti ověřování, které jsou k dispozici Internetové informační služby (IIS). Klienti WCF je nepodporují. Pokud služba musí být zabezpečená, použijte možnosti poskytované WCF, protože tyto možnosti jsou odolnější a jsou založeny na standardních protokolů.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Dopad na výkon způsobené načítání ServiceModel HttpModule  
 V rozhraní .NET Framework 3.0 WCF `HttpModule` byla nainstalovaná v kořenovém souboru Web.config tak, aby každá aplikace technologie ASP.NET byla povolena WCF. To může ovlivnit výkon, takže můžete odebrat `ServiceModel` pro soubor Web.config, jak je znázorněno v následujícím příkladu.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
