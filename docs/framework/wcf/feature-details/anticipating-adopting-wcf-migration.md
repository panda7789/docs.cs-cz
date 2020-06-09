---
title: 'Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: b43f509bd49ebe89d7ed0be4c37b3ed179aaeb8c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576496"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace
Chcete-li zajistit snazší budoucí migraci nových aplikací ASP.NET do služby WCF, postupujte podle předchozích doporučení a také následujících doporučení.  
  
## <a name="protocols"></a>Protokoly  
 Zakažte podporu ASP.NET 2.0 pro SOAP 1,2:  
  
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
  
 Doporučuje se to proto, že WCF vyžaduje zprávy, které odpovídají různým protokolům, jako jsou SOAP 1,1 a SOAP 1,2, pro přechod pomocí různých koncových bodů. Pokud je webová služba ASP.NET 2,0 nakonfigurovaná tak, aby podporovala SOAP 1,1 i SOAP 1,2, což je výchozí konfigurace, pak nemůže být migrována do jednoho koncového bodu WCF na původní adrese, která by byla určitě kompatibilní se všemi stávajícími klienty webové služby ASP.NET. Také výběr protokolu SOAP 1,2 namísto 1,1 bude vážně omezovat Clientele služby.  
  
## <a name="service-development"></a>Vývoj služeb  
 Služba WCF umožňuje definovat kontrakty služby použitím <xref:System.ServiceModel.ServiceContractAttribute> rozhraní nebo na třídy. Doporučuje se použít atribut na rozhraní, nikoli na třídu, protože tím vznikne definice kontraktu, který může být různým způsobem implementován libovolným počtem tříd. ASP.NET 2,0 podporuje možnost použití <xref:System.Web.Services.WebService> atributu na rozhraní i třídy. Jak již bylo zmíněno, existuje vada v ASP.NET 2,0, kdy parametr namespace <xref:System.Web.Services.WebService> atributu nemá žádný vliv, pokud je tento atribut použit na rozhraní, nikoli na třídu. Vzhledem k tomu, že je obecně vhodné změnit obor názvů služby z výchozí hodnoty, `http://tempuri.org` použijte parametr oboru názvů <xref:System.Web.Services.WebService> atributu, jeden by měl pokračovat v definování ASP.NET webových služeb použitím <xref:System.ServiceModel.ServiceContractAttribute> atributu buď na rozhraní nebo na třídy.  
  
- Musí mít co nejmenší kód v metodách, pomocí kterých jsou tato rozhraní definována. Přidělí jim svou práci na jiné třídy. Nové typy služeb WCF by pak mohly delegovat svou podstatnou práci na tyto třídy.  
  
- Zadejte explicitní názvy operací služby pomocí `MessageName` parametru <xref:System.Web.Services.WebMethodAttribute> .  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     To je důležité, protože výchozí názvy pro operace v ASP.NET se liší od výchozích názvů dodaných službou WCF. Zadáním explicitních názvů předejdete tomu, že se spoléháte na výchozí hodnoty.  
  
- Neimplementujte operace webové služby ASP.NET s polymorfními metodami, protože WCF nepodporuje implementaci operací pomocí polymorfních metod.  
  
- Použijte <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> k zadání explicitních hodnot hlaviček protokolu HTTP SOAPAction, podle kterých budou požadavky HTTP směrovány na metody.  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Díky tomuto přístupu se postará, že se musí spoléhat na výchozí hodnoty SOAPAction používané ASP.NET a WCF.  
  
- Nepoužívejte rozšíření SOAP. Pokud jsou požadovány rozšíření SOAP, určete, zda je účel, pro který jsou zvažovány, funkce, která je již součástí služby WCF. V takovém případě je vhodné znovu zvážit možnost nepřijmout WCF hned.  
  
## <a name="state-management"></a>Správa stavu  
 Nemusíte se starat o stav ve službách. Nejen udržují stav za následek ohrožení škálovatelnosti aplikace, ale mechanismy správy stavů ASP.NET a WCF se velmi liší, i když WCF podporuje mechanismy ASP.NET v režimu kompatibility ASP.NET.  
  
## <a name="exception-handling"></a>Zpracování výjimek  
 V návrhu struktur datových typů, které mají být zasílány a přijímány službou, také Navrhněte struktury, které reprezentují různé typy výjimek, které mohou nastat v rámci služby, které může chtít předat klientovi.  
  
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
  
 Poskytněte takové třídy schopnost serializace do XML:  
  
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
  
 Třídy pak mohou být použity k poskytnutí podrobností pro explicitně vygenerované <xref:System.Web.Services.Protocols.SoapException> instance:  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Tyto třídy výjimek budou snadno použitelné s <xref:System.ServiceModel.FaultException%601> třídou WCF k vyvolání nového`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Zabezpečení  
 Níže jsou uvedená některá doporučení zabezpečení.  
  
- Nepoužívejte profily ASP.NET 2,0, protože by je bylo možné použít při migraci služby na WCF.  
  
- Nepoužívejte seznamy ACL k řízení přístupu ke službám, protože webové služby ASP.NET podporují seznamy ACL pomocí služby Internetová informační služba (IIS), služba WCF nefunguje – protože webové služby ASP.NET závisejí na službě IIS pro hostování a služba WCF nemusí nutně být hostovaná ve službě IIS.  
  
- Zvažte použití zprostředkovatelů rolí ASP.NET 2,0 pro autorizaci přístupu k prostředkům služby.  
  
## <a name="see-also"></a>Viz také

- [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace](anticipating-adopting-the-wcf-easing-future-integration.md)
