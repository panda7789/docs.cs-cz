---
title: 'Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 995bdaaaba96bf8697ea75c1f1a17fa8e51ec2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185474"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace
Chcete-li zajistit snadnější budoucí migraci nových aplikací ASP.NET do WCF, postupujte podle předchozích doporučení a následující doporučení.  
  
## <a name="protocols"></a>Protokoly  
 Zakažte ASP.NET 2.0 podpora soap 1.2:  
  
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
  
 To je vhodné, protože WCF vyžaduje zprávy, které odpovídají různým protokolům, jako je SOAP 1.1 a SOAP 1.2, pro použití různých koncových bodů. Pokud je webová služba ASP.NET 2.0 nakonfigurována tak, aby podporovala rozhraní SOAP 1.1 i SOAP 1.2, což je výchozí konfigurace, nelze ji migrovat dopředu na jeden koncový bod WCF na původní adrese, která by byla jistě kompatibilní se všemi ASP.NET web stávajících klientů služby. Také výběr SOAP 1.2 namísto 1.1 bude více vážně omezit klientelu služby.  
  
## <a name="service-development"></a>Vývoj služeb  
 WCF umožňuje definovat servisní smlouvy <xref:System.ServiceModel.ServiceContractAttribute> použitím buď rozhraní nebo třídy. Doporučuje se použít atribut rozhraní spíše než na třídu, protože tím vytvoří definici smlouvy, která může být různě implementována libovolným počtem tříd. ASP.NET 2.0 podporuje možnost <xref:System.Web.Services.WebService> použití atributu rozhraní i tříd. Však jak již bylo zmíněno, je vada v ASP.NET 2.0, podle kterého Namespace parametr <xref:System.Web.Services.WebService> atribut nemá žádný vliv, pokud je tento atribut použit rozhraní spíše než třídy. Vzhledem k tomu, `http://tempuri.org`že je obecně vhodné změnit obor názvů služby z <xref:System.Web.Services.WebService> výchozí hodnoty , pomocí parametru Obor <xref:System.ServiceModel.ServiceContractAttribute> názvů atributu, je třeba pokračovat v definování ASP.NET webových služeb použitím atributu buď na rozhraní, nebo na třídy.  
  
- Mají co nejméně kódu v metodách, kterými jsou definovány tyto rozhraní. Nechte je delegovat svou práci na jiné třídy. Nové typy služeb WCF pak mohou také delegovat svou věcnou práci na tyto třídy.  
  
- Zadejte explicitní názvy pro operace `MessageName` služby <xref:System.Web.Services.WebMethodAttribute>pomocí parametru .  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Je to důležité, protože výchozí názvy operací v ASP.NET se liší od výchozích názvů poskytnutých WCF. Poskytnutím explicitních názvů se vyhnete spoléhání se na výchozí názvy.  
  
- Neimplementujte operace ASP.NET webové služby pomocí polymorfních metod, protože WCF nepodporuje implementaci operací pomocí polymorfních metod.  
  
- Slouží <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> k zadání explicitních hodnot pro hlavičky SOAPAction HTTP, kterými budou požadavky HTTP směrovány na metody.  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Vezmeme-li tento přístup bude obcházení museli spoléhat na výchozí SOAPAction hodnoty používané ASP.NET a WCF jsou stejné.  
  
- Nepoužívejte rozšíření SOAP. Pokud soap rozšíření jsou požadovány, pak určit, zda účel, pro který jsou považovány za je funkce, která je již k dispozici WCF. Pokud tomu tak skutečně je, pak přehodnotit volbu nepřijmout WCF hned.  
  
## <a name="state-management"></a>Správa státu  
 Vyhněte se nutnosti udržovat stav ve službách. Nejen, že udržování stavu mají tendenci ohrozit škálovatelnost aplikace, ale mechanismy správy stavu ASP.NET a WCF jsou velmi odlišné, i když WCF podporuje ASP.NET mechanismy v režimu kompatibility ASP.NET.  
  
## <a name="exception-handling"></a>Zpracování výjimek  
 Při navrhování struktury datových typů, které mají být odeslány a přijaty službou, také návrhové struktury představují různé typy výjimek, které mohou nastat v rámci služby, které by bylo možné chtít předat klientovi.  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException
{
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation
    {  
        get {
            return this.anticipatedExceptionInformationField;  
        }  
        set {  
            this.anticipatedExceptionInformationField = value;  
        }  
    }  
}  
```  
  
 Poznejte těmto třídám možnost serializovat se do XML:  
  
```csharp  
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
  
 Třídy pak lze poskytnout podrobnosti pro <xref:System.Web.Services.Protocols.SoapException> explicitně vyvolána instance:  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Tyto třídy výjimek budou snadno opakovaně použitelné <xref:System.ServiceModel.FaultException%601> s třídou WCF, aby vyvolaly novou`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Zabezpečení  
 Následují některá doporučení zabezpečení.  
  
- Nepoužívejte ASP.NET profily 2.0, protože jejich použití by omezilo použití režimu integrace ASP.NET, pokud by služba byla migrována do WCF.  
  
- Nepoužívejte přístupové sítě ACL k řízení přístupu ke službám, protože ASP.NET webové služby podporují seznamu ACL používající internetové informační služby (IIS), wcf nikoli – protože ASP.NET webové služby závisí na službě IIS pro hostování a wcf nemusí být nutně hostován ve službě IIS.  
  
- Zvažte použití ASP.NET 2.0 zprostředkovatelé rolí pro autorizaci přístupu k prostředkům služby.  
  
## <a name="see-also"></a>Viz také

- [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
