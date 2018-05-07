---
title: 'Očekávání přechodu služby Windows Communication Foundation: usnadnění budoucí migrace'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: aeafc164d16d9dc60ad0b3012da292e9b0bb38b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Očekávání přechodu služby Windows Communication Foundation: usnadnění budoucí migrace
Aby jednodušší budoucí migrace nové aplikace ASP.NET na WCF, postupujte podle předchozích doporučení a také následující doporučení.  
  
## <a name="protocols"></a>protokoly  
 Zakažte podporu technologie ASP.NET 2.0 pro SOAP 1.2:  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>    
      </webServices>  
     </system.web>   
</configuration>  
```  
  
 Díky tomu se nedoporučuje, protože vyžaduje zprávy, které odpovídají různé protokoly, jako je SOAP 1.1 a SOAP 1.2 přejít pomocí různých koncových bodů WCF. Pokud 2.0 ASP.NET – webové služby je nakonfigurován pro podporu protokolu SOAP 1.1 a SOAP 1.2, což je výchozí konfigurace a nemůže být migrovali předat dál na jeden koncový bod WCF na původní adrese, která by určitě být kompatibilní se všemi technologie ASP.NET existující klienti služby. Také výběr SOAP 1.2 místo 1.1 více značně omezí zákazníků služby.  
  
## <a name="service-development"></a>Vývoj pro služby  
 WCF umožňuje definování kontraktů služby s použitím <xref:System.ServiceModel.ServiceContractAttribute> na rozhraní nebo třídy. Doporučujeme použít atribut rozhraní, nikoli třída, protože je to proto vytvoří definici kontraktu, která může být libovolný počet třídy různě implementována. ASP.NET 2.0 podporuje možnost použít <xref:System.Web.Services.WebService> atribut rozhraní a také třídy. Jak už bylo zmíněno, je však značit potíže v aplikaci ASP.NET 2.0, podle kterého parametr Namespace <xref:System.Web.Services.WebService> atribut nemá žádný vliv, pokud tento atribut se použije na rozhraní než třídu. Vzhledem k tomu, že je většinou vhodné změnit obor názvů služby z výchozí hodnoty, http://tempuri.org, pomocí parametru Namespace <xref:System.Web.Services.WebService> atribut jeden by měly pokračovat definování webových služeb ASP.NET s použitím <xref:System.ServiceModel.ServiceContractAttribute> Atribut rozhraní nebo třídy.  
  
-   Mají jako málo kód jako možný metody, které jsou definovány těchto rozhraní. Kliknul delegovat práci na jiné třídy. Nové typy služby WCF pak rovněž delegovat práci podstatné do těchto tříd.  
  
-   Zadat explicitní názvy pro operace služby pomocí `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Díky tomu je důležité, protože výchozí názvy pro operace v technologii ASP.NET se liší od výchozí názvy poskytl WCF. Poskytnutím explicitní názvy neměli spoléhat na výchozí hodnoty.  
  
-   Neimplementuje operace ASP.NET webové služby s polymorfním metodami, protože WCF nepodporuje implementující operace s polymorfním metody.  
  
-   Použití <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> zadat explicitní hodnoty pro hlavičky SOAPAction HTTP, pomocí které protokolu HTTP, budou směrovány požadavky na metody.  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Tento postup trvá obejít museli spoléhat na výchozí hodnoty SOAPAction používané technologie ASP.NET a WCF se stejné.  
  
-   Vyhněte se používá rozšíření SOAP. Pokud rozšíření SOAP, pak určete, zda pro který je právě považována za účelem je funkce, která je již poskytované WCF. Pokud tomu tak je skutečně, pak znovu volba není hned přijmout službu WCF.  
  
## <a name="state-management"></a>Stav správy  
 Nemuseli dělat údržbu stavu služby. Pouze nemá zachování stavu mívají ohrozit škálovatelnost aplikace, ale mechanismy řízení stavu technologie ASP.NET a WCF se velmi liší, i když WCF podporovat mechanismy ASP.NET v režimu kompatibility ASP.NET.  
  
## <a name="exception-handling"></a>Zpracování výjimek  
 Při navrhování struktury typy dat, které mají odesílat a přijímat přes službu, také návrhu struktury k reprezentaci různých typů výjimek, které můžou nastat v rámci služby než chtít předávaným klienta.  
  
```  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 Poskytněte těchto tříd možnost sami serializaci do formátu XML:  
  
```  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 Třídy pak lze upravit podrobnosti pro explicitně vyvolána <xref:System.Web.Services.Protocols.SoapException> instancí:  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Tyto třídy výjimek bude snadno opakovaně použitelné s WCF<xref:System.ServiceModel.FaultException%601> třída má být vyvolána nová `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Zabezpečení  
 Následuje několik doporučení zabezpečení.  
  
-   Vyhněte se použití profilů technologie ASP.NET 2.0, jako je pomocí by omezit použití režimu integrace ASP.NET, pokud došlo k migraci služby WCF.  
  
-   Nepoužívejte seznamy řízení přístupu k řízení přístupu ke službám, jako rozhraní ASP.NET Web services podporuje seznamy ACL pomocí Internetové informační služby (IIS), WCF nemá – protože webových služeb ASP.NET závisí na službě IIS pro hostování a WCF nutně nemusí být hostovaný ve službě IIS.  
  
-   Zvažte použití zprostředkovatelů rolí prostředí ASP.NET 2.0 pro ověřování přístupu k prostředkům služby.  
  
## <a name="see-also"></a>Viz také  
 [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
