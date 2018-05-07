---
title: 'Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: f81e158a5e7f897307c0c6d376dfe01dac127ead
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace
Pokud jste ještě dnes pomocí technologie ASP.NET a předvídat pomocí WCF v budoucnu, toto téma obsahuje pokyny k zajištění, že nové rozhraní ASP.NET Web services bude fungovat i společně s aplikací služby WCF.  
  
## <a name="general-recommendations"></a>Obecná doporučení  
 Přijmout technologii ASP.NET 2.0 pro všechny nové služby. Díky tomu bude poskytovat přístup k vylepšení a vylepšení nové verze. Však bude taky povolit možnost pomocí technologie ASP.NET 2.0 součásti společně s součásti WCF ve stejné aplikaci.  
  
## <a name="protocols"></a>protokoly  
 Použít technologii ASP.NET 2.0 nové zařízení pro ověřování shody pro služby WS-I Basic Profile 1.1:  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 ASP.NET – webové služby, které v souladu s WS-I Basic Profile 1.1 pomocí předdefinovaných WCF vazbu, bude umožňuje vzájemnou spolupráci s klienty WCF <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Vývoj pro služby  
 Nepoužívejte <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut tak, aby měl zprávy směrované na metody založené na plně kvalifikovaný název prvku body zprávu protokolu SOAP a ne záhlaví SOAPAction HTTP. WCF používá hlavičky protokolu HTTP SOAPAction pro směrování zpráv.  
  
## <a name="data-representation"></a>Reprezentace dat  
 Zadaný kód XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky stejný jako soubor XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu zadaný obor názvů pro soubor XML byl explicitně definován. Při definování datový typ pro použití s webovými službami ASP.NET v očekávání přijetí WCF v budoucnu, postupujte takto:  
  
1.  Definování typu pomocí třídy rozhraní .NET Framework, nikoli schématu XML.  
  
2.  Přidat pouze <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.XmlRootAttribute> k třídě, pomocí k tomu explicitně zadat obor názvů pro typ. Provést žádné přidat další atributy z <xref:System.Xml.Serialization> obor názvů řídit, jak se přeložit na XML třídy rozhraní .NET Framework.  
  
 Přijetím tuto metodu, musí mít možnost později provádět třídy rozhraní .NET do kontrakty dat s přidáním systému <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> beze změny výrazně XML, do které se serializují třídy pro přenos. Typy použité ve zprávách webových služeb ASP.NET bude možno zpracovat jako kontrakty dat aplikace WCF je mezi další výhody, lepší výkon v aplikacích WCF.  
  
## <a name="security"></a>Zabezpečení  
 Nepoužívejte možnosti ověřování zadané Internetové informační služby (IIS). Klienti WCF je nepodporují. Pokud služba musí být zabezpečené, pomocí možnosti poskytované WCF, protože tyto možnosti jsou bohatší a je založený na standardních protokolů.  
  
## <a name="see-also"></a>Viz také  
 [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
