---
title: Interoperabilita s webovými službami ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 8a0737a36989dd8bc6f5d5670555c7b2218798bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="interoperability-with-aspnet-web-services"></a>Interoperabilita s webovými službami ASP.NET
Vzájemná funkční spolupráce mezi [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby a služby Windows Communication Foundation (WCF) webové služby lze dosáhnout zajistíte, že služby implementovaná pomocí obou technologií odpovídají WS-I Basic Profile 1.1 specifikace. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Webové služby, které odpovídají WS-I Basic Profile 1.1 jsou umožňuje vzájemnou spolupráci s klienty WCF pomocí vazby poskytované systémem WCF, <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Použití [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] možnost přidání <xref:System.Web.Services.WebService> a <xref:System.Web.Services.WebMethodAttribute> atributy rozhraní, nikoli třída a zápis třídu pro implementaci rozhraní, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Tato možnost je upřednostňované, protože rozhraní s <xref:System.Web.Services.WebService> atribut se považuje za kontraktu pro operace prováděné na službu, kterou lze opětovně použít s různými třídami, které může implementovat stejné kontraktu různými způsoby.  
  
 Nepoužívejte <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut tak, aby měl zprávy směrované na metody založené na plně kvalifikovaný název elementu těla protokolu SOAP zprávy místo `SOAPAction` hlavičky protokolu HTTP. Používá WCF `SOAPAction` hlavičky protokolu HTTP pro směrování zpráv.  
  
 Zadaný kód XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky stejný jako soubor XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu zadaný obor názvů pro soubor XML byl explicitně definován. Při definování datový typ pro použití s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]webové služby v očekávání přijetí WCF, postupujte takto:  
  
-   Definování typu pomocí třídy rozhraní .NET Framework, nikoli schématu XML.  
  
-   Přidat pouze <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.XmlRootAttribute> k třídě, pomocí k tomu explicitně zadat obor názvů pro typ. Nepřidávejte další atributy z <xref:System.Xml.Serialization> obor názvů řídit, jak se přeložit na XML třídy rozhraní .NET Framework.  
  
-   Přijetím tuto metodu, musí mít možnost později provádět třídy rozhraní .NET do kontrakty dat s přidáním systému <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> beze změny výrazně XML, do které se serializují třídy pro přenos. Typy používané ve zprávách podle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby může zpracovat jako kontrakty dat aplikací služby WCF, je lepší výkon v aplikacích WCF mezi další výhody.  
  
 Nepoužívejte možnosti ověřování zadané Internetové informační služby (IIS). Klienti WCF je nepodporují. Pokud služba musí být zabezpečená, použijte možnosti poskytované WCF, protože tyto možnosti jsou robustní a je založený na standardních protokolů.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Dopad na výkon způsobené načítání modulu HTTP ServiceModel  
 V rozhraní .NET Framework 3.0, WCF `HttpModule` byl nainstalován v kořenovém souboru Web.config, tak, aby každá aplikace ASP.NET byl WCF povolena. To může ovlivnit výkon, takže můžete odebrat `ServiceModel` pro soubor Web.config, jak je znázorněno v následujícím příkladu.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
