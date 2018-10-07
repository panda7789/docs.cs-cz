---
title: 'Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí migrace'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 171a31b375eae4c032849c2a1c2090f5d9ff856f
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837382"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí migrace
Aby jednodušší budoucí migrace z nové aplikace ASP.NET na WCF, postupujte podle předchozí doporučení, jakož i následující doporučení.  
  
## <a name="protocols"></a>Protokoly  
 Zakážete podporu protokolu SOAP 1.2 ASP.NET 2.0:  
  
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
  
 Tím se doporučuje, protože vyžaduje zprávy, které odpovídají různé protokoly, jako je protokol SOAP 1.1 a SOAP 1.2, přejděte pomocí různých koncových bodů WCF. Pokud webového rozhraní ASP.NET 2.0, služba je nakonfigurována pro podporu protokolu SOAP 1.1 a SOAP 1.2, což je výchozí konfigurace, pak jej nelze migrovat vpřed na jednom koncovém bodu WCF na původní adrese, která by byla jistě být kompatibilní se všemi ASP.NET Web existující klienti služby. Také výběrem SOAP 1.2 místo 1.1 více vážně omezí zákazníků služby.  
  
## <a name="service-development"></a>Vývoj služby  
 WCF umožňuje definování kontraktů služby s použitím <xref:System.ServiceModel.ServiceContractAttribute> rozhraní nebo tříd. Doporučujeme použít atribut rozhraní, nikoli třída, protože to uděláte tak vytvoří definici kontraktu, která může být libovolný počet tříd různě implementována. Technologie ASP.NET 2.0 podporuje možnost použít <xref:System.Web.Services.WebService> atribut rozhraní, stejně jako třídy. Jak již bylo zmíněno, existuje ale vadu v technologii ASP.NET 2.0, podle kterého parametru Namespace <xref:System.Web.Services.WebService> atribut nemá žádný vliv při použití atributu na rozhraní namísto třídy. Protože je obecně vhodné změnit obor názvů služby z výchozí hodnoty `http://tempuri.org`, pomocí parametru Namespace <xref:System.Web.Services.WebService> atribut, jeden by měl pokračovat definování webových služeb ASP.NET s použitím <xref:System.ServiceModel.ServiceContractAttribute> Atribut rozhraní nebo tříd.  
  
-   Metody, které jsou definovány těchto rozhraní je možné máte jako malým množstvím kódu. Požádejte svou práci do jiné třídy delegáta. Nový typ služby WCF pak rovněž delegovat práci nepotřebují důležité do těchto tříd.  
  
-   Zadat explicitní názvy pro operace využívání služby `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     To je důležité, protože se liší od výchozí názvy poskytnutých WCF výchozí názvy pro operace v technologii ASP.NET. Poskytnutím explicitní názvy neměli spoléhat na výchozí hodnoty.  
  
-   Neprovádějte implementaci operace služby rozhraní ASP.NET Web s polymorfní metody, protože WCF nepodporuje implementaci operace s polymorfní metody.  
  
-   Použití <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> zadat explicitní hodnoty záhlaví SOAPAction HTTP, pomocí které protokolu HTTP se budou směrovat požadavky do metody.  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Tento postup zajistí obejde museli spoléhat na výchozí hodnoty SOAPAction používané technologie ASP.NET a WCF se stejné.  
  
-   Vyhněte se použití rozšíření SOAP. Pokud rozšíření SOAP, pak určete, zda je účely, pro které jsou právě považovány za funkce, která je již poskytované WCF. Pokud se ve skutečnosti je to tento případ, pak zvažte možnost, které nejsou hned přijmout WCF.  
  
## <a name="state-management"></a>Správa stavu  
 Vyhněte se nutnosti udržovat stav služby. Pouze nemá zachování stavu vést k ohrožení škálovatelnost aplikace, ale stav mechanismy správy technologie ASP.NET a WCF jsou velmi odlišné, i když WCF podporovat mechanismy ASP.NET v režim kompatibility ASP.NET.  
  
## <a name="exception-handling"></a>Zpracování výjimek  
 Při navrhování struktury datové typy na odeslané a přijaté službou, také návrh struktury tak, aby představují různé typy výjimek, které mohou nastat v rámci služby, že jedna možná budete chtít sdělit do klienta.  
  
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
  
 Umožnit takové třídy sami serializaci do formátu XML:  
  
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
  
 Třídy pak umožňuje zadejte podrobnosti pro explicitně vyvolána <xref:System.Web.Services.Protocols.SoapException> instancí:  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Tyto třídy výjimek bude snadno opakovaně použitelné s WCF<xref:System.ServiceModel.FaultException%601> třídy k vyvolání nové `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Zabezpečení  
 Následují některá doporučení zabezpečení.  
  
-   Vyhněte se použití profilů ASP.NET 2.0, jako je použití by omezit použití režim integrace ASP.NET Pokud služby byl migrován a WCF.  
  
-   Vyhněte se použití seznamů ACL pro řízení přístupu ke službám, jako rozhraní ASP.NET Web services podporuje seznamy řízení přístupu pomocí Internetové informační služby (IIS), WCF nepodporuje, protože rozhraní ASP.NET Web services závisí na službě IIS pro hostování a WCF nutně nemusí být hostovaná ve službě IIS.  
  
-   Zvažte použití zprostředkovatele rolí ASP.NET 2.0 pro ověřování přístupu k prostředkům služby.  
  
## <a name="see-also"></a>Viz také  
 [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
