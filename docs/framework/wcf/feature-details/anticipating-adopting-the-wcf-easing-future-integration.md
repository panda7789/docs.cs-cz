---
title: 'Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: 6392194b3124c999031123225dcc28c8de6171e9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576522"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace
Pokud používáte ASP.NET ještě dnes a předpokládáte pomocí WCF v budoucnu, toto téma poskytuje pokyny, abyste zajistili, že budou nové webové služby ASP.NET fungovat dobře společně s aplikacemi WCF.  
  
## <a name="general-recommendations"></a>Obecná doporučení  
 Pro všechny nové služby se ASP.NET 2,0. Tím zajistíte přístup k vylepšením a vylepšením nové verze. Zároveň ale umožní využít komponenty ASP.NET 2,0 společně s komponentami WCF ve stejné aplikaci.  
  
## <a name="protocols"></a>Protokoly  
 Použijte nové zařízení ASP.NET 2.0 k ověření shody s profilem WS-I Basic 1,1:  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Webové služby ASP.NET, které odpovídají profilu WS-I Basic Profile 1,1, budou spolupracovat s klienty WCF pomocí předdefinované vazby WCF <xref:System.ServiceModel.BasicHttpBinding> .  
  
## <a name="service-development"></a>Vývoj služeb  
 Nepoužívejte <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut ke směrování zpráv na metody založené na plně kvalifikovaném názvu prvku těla zprávy SOAP, nikoli v hlavičce SOAPACTION http. WCF používá pro směrování zpráv hlavičku HTTP SOAPAction.  
  
## <a name="data-representation"></a>Reprezentace dat  
 KÓD XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> je ve výchozím nastavení serializován typ, je sémanticky totožný s XML, do kterého je <xref:System.Runtime.Serialization.DataContractSerializer> serializován typ, za předpokladu, že obor názvů XML je explicitně definován. Při definování datového typu pro použití s webovými službami ASP.NET při předvídání budoucího přijetí WCF v budoucnu udělejte toto:  
  
1. Definujte typ pomocí .NET Framework třídy místo schématu XML.  
  
2. Přidejte pouze <xref:System.SerializableAttribute> <xref:System.Xml.Serialization.XmlRootAttribute> třídu a ke třídě pomocí druhé k explicitnímu definování oboru názvů pro daný typ. Neprovádějte přidávání dalších atributů z <xref:System.Xml.Serialization> oboru názvů, abyste mohli řídit, jak se má třída .NET Framework přeložit do XML.  
  
 Přijetím tohoto přístupu byste měli být schopni později převést třídy .NET na kontrakty dat s přidáním <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> bez významně měnit kód XML, do kterého jsou třídy serializovány pro přenos. Typy používané ve zprávách podle ASP.NET webové služby budou možné zpracovávat jako kontrakty dat aplikacemi WCF, a to mimo jiné výhody a lepší výkon v aplikacích WCF.  
  
## <a name="security"></a>Zabezpečení  
 Nepoužívejte možnosti ověřování poskytované Internetová informační služba (IIS). Klienti WCF je nepodporují. Pokud musí být služba zabezpečená, použijte možnosti poskytované službou WCF, protože tyto možnosti jsou bohatší a jsou založené na standardních protokolech.  
  
## <a name="see-also"></a>Viz také

- [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace](anticipating-adopting-wcf-migration.md)
