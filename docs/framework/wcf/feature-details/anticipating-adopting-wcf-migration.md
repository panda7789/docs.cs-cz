---
title: "Očekávání přechodu služby Windows Communication Foundation: usnadnění budoucí migrace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76770eff76a7a641ee853f314b5d2c14a56737c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Očekávání přechodu služby Windows Communication Foundation: usnadnění budoucí migrace
K zajištění jednodušší budoucí migrace nové aplikace ASP.NET na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], postupujte podle předchozích doporučení a také následující doporučení.  
  
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
  
 Díky tomu se doporučuje protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyžaduje zprávy, které odpovídají různé protokoly, jako je SOAP 1.1 a SOAP 1.2 přejít pomocí různými koncovými body. Pokud technologie ASP.NET 2.0 webové služby je nakonfigurována pro podporu protokolu SOAP 1.1 a SOAP 1.2, což je výchozí konfigurace, potom ji nelze předat dál migrovat na jedné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod na původní adresu, která by jistě kompatibilní se všemi ASP Stávající klienty .NET webové služby. Také výběr SOAP 1.2 místo 1.1 více značně omezí zákazníků služby.  
  
## <a name="service-development"></a>Vývoj pro služby  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]slouží k definování kontraktů služby s použitím <xref:System.ServiceModel.ServiceContractAttribute> na rozhraní nebo třídy. Doporučujeme použít atribut rozhraní, nikoli třída, protože je to proto vytvoří definici kontraktu, která může být libovolný počet třídy různě implementována. ASP.NET 2.0 podporuje možnost použít <xref:System.Web.Services.WebService> atribut rozhraní a také třídy. Jak už bylo zmíněno, je však značit potíže v aplikaci ASP.NET 2.0, podle kterého parametr Namespace <xref:System.Web.Services.WebService> atribut nemá žádný vliv, pokud tento atribut se použije na rozhraní než třídu. Protože je většinou vhodné změnit obor názvů služby z výchozí hodnoty, http://tempuri.org, pomocí parametru Namespace <xref:System.Web.Services.WebService> atribut jeden by měly pokračovat definování webových služeb ASP.NET s použitím <xref:System.ServiceModel.ServiceContractAttribute> Atribut rozhraní nebo třídy.  
  
-   Mají jako málo kód jako možný metody, které jsou definovány těchto rozhraní. Kliknul delegovat práci na jiné třídy. Nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] typů služeb pak rovněž delegovat práci podstatné do těchto tříd.  
  
-   Zadat explicitní názvy pro operace služby pomocí `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Díky tomu je důležité, protože výchozí názvy pro operace v technologii ASP.NET se liší od výchozí názvy poskytl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Poskytnutím explicitní názvy neměli spoléhat na výchozí hodnoty.  
  
-   Neimplementuje operace ASP.NET webové služby s polymorfním metodami, protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nepodporuje implementující operace s polymorfním metody.  
  
-   Použití <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> zadat explicitní hodnoty pro hlavičky SOAPAction HTTP, pomocí které protokolu HTTP, budou směrovány požadavky na metody.  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Tento postup trvá obejde museli spoléhat na výchozí hodnoty SOAPAction použitý technologií ASP.NET a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se stejné.  
  
-   Vyhněte se používá rozšíření SOAP. Pokud rozšíření SOAP, pak určit, zda pro který je právě považována za účelem je funkce, která je již poskytované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Pokud tomu tak je skutečně, nebyla volba není přijmout [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hned.  
  
## <a name="state-management"></a>Stav správy  
 Nemuseli dělat údržbu stavu služby. Zachování stavu nejen mívají ohrozit škálovatelnost aplikace, ale mechanismy řízení stavu technologie ASP.NET a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se příliš neliší, i když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje mechanismy ASP.NET v režim kompatibility ASP.NET režim.  
  
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
  
 Tyto třídy výjimek, bude se snadno opakovaně použitelné[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.FaultException%601> třída má být vyvolána nová`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Zabezpečení  
 Následuje několik doporučení zabezpečení.  
  
-   Vyhněte se použití profilů technologie ASP.NET 2.0, jako je pomocí by omezit použití režimu integrace ASP.NET, pokud došlo k migraci služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Vyhněte se použití seznamů řízení přístupu k řízení přístupu ke službám, jako webových služeb ASP.NET podporuje seznamy ACL pomocí Internetové informační služby (IIS), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nemá – protože webových služeb ASP.NET závisí na službě IIS pro hostování a WCF nutně nemusí být hostovaný ve službě IIS.  
  
-   Zvažte použití zprostředkovatelů rolí prostředí ASP.NET 2.0 pro ověřování přístupu k prostředkům služby.  
  
## <a name="see-also"></a>Viz také  
 [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
