---
title: 'Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: f4cc450b04fd05d390a1f41f3d14c19f4b23be29
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296488"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace
Pokud používáte ASP.NET a předvídat pomocí technologie WCF v budoucnu, toto téma obsahuje pokyny pro zajištění, že nové technologie ASP.NET webové služby bude fungovat dobře spolu s aplikací služby WCF.  
  
## <a name="general-recommendations"></a>Obecná doporučení  
 Osvojte si technologii ASP.NET 2.0 pro všechny nové služby. To zajistí přístup k vylepšení a rozšíření na novou verzi. Ale vám také umožní možnost použití komponent v technologii ASP.NET 2.0 společně s WCF komponenty ve stejné aplikaci.  
  
## <a name="protocols"></a>Protokoly  
 Použití nového zařízení technologie ASP.NET 2.0 pro ověřování shody WS-I Basic Profile 1.1:  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Webových služeb ASP.NET, které odpovídají WS-I Basic Profile 1.1 pomocí WCF předdefinovaných vazeb, bude spolupracují se službou WCF klienti <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Vývoj služby  
 Vyhněte se použití <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut zprávy směruje do metody podle plně kvalifikovaný název elementu těla zprávy protokolu SOAP a ne záhlaví SOAPAction HTTP. Záhlaví SOAPAction HTTP WCF používá pro směrování zpráv.  
  
## <a name="data-representation"></a>Reprezentace dat  
 XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky shodná s XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podle oboru názvů XML není výslovně uveden. Po definování typu dat pro použití s webovými službami ASP.NET čekat na případná přijetí WCF v budoucnu, postupujte takto:  
  
1.  Definování typů pomocí tříd rozhraní .NET Framework než schématu XML.  
  
2.  Přidat pouze <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.XmlRootAttribute> na třídu pomocí odkazující k explicitnímu definování oboru názvů typu. Provést žádné přidat další atributy z <xref:System.Xml.Serialization> obor názvů řídit, jak je třída rozhraní .NET Framework mají být převedeny do jazyka XML.  
  
 Přijetím tohoto přístupu by měl být schopen později provést třídy rozhraní .NET v kontraktech dat a uveďte <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> beze změny výrazně XML, do které třídy serializují pro přenos. Typy použité ve zprávách webových služeb ASP.NET s budou moci zpracovat jako kontraktů dat aplikací služby WCF, což má za následek, mezi další výhody, lepší výkon v aplikacích WCF.  
  
## <a name="security"></a>Zabezpečení  
 Vyhněte se použití možnosti ověřování, které jsou k dispozici Internetové informační služby (IIS). Klienti WCF je nepodporují. Pokud služba musí být zabezpečené, pomocí možností poskytnutých WCF, protože tyto možnosti jsou bohatší a jsou založeny na standardních protokolů.  
  
## <a name="see-also"></a>Viz také  
 [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
