---
title: "Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8f60b2566895acfd7d2b749729fab9c3f5deb20c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace
Pokud jste ještě dnes pomocí technologie ASP.NET a předvídat pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v budoucnu, toto téma obsahuje pokyny k zajištění, že nové rozhraní ASP.NET Web services bude fungovat dobře společně s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.  
  
## <a name="general-recommendations"></a>Obecná doporučení  
 Přijmout technologii ASP.NET 2.0 pro všechny nové služby. Díky tomu bude poskytovat přístup k vylepšení a vylepšení nové verze. Však bude taky povolit možnost pomocí technologie ASP.NET 2.0 součásti společně s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] součásti ve stejné aplikaci.  
  
## <a name="protocols"></a>protokoly  
 Použít technologii ASP.NET 2.0 nové zařízení pro ověřování shody pro služby WS-I Basic Profile 1.1:  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 ASP.NET – webové služby, které v souladu s WS-I Basic Profile 1.1 bude vzájemná spolupráce s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienty pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] předdefinované vazby, <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Vývoj pro služby  
 Nepoužívejte <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut tak, aby měl zprávy směrované na metody založené na plně kvalifikovaný název prvku body zprávu protokolu SOAP a ne záhlaví SOAPAction HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]záhlaví SOAPAction HTTP používá pro směrování zpráv.  
  
## <a name="data-representation"></a>Reprezentace dat  
 Zadaný kód XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky stejný jako soubor XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu zadaný obor názvů pro soubor XML byl explicitně definován. Při definování datový typ pro použití s rozhraním ASP.NET Web services v očekávání přijetí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v budoucnu, postupujte takto:  
  
1.  Definování typu pomocí třídy rozhraní .NET Framework, nikoli schématu XML.  
  
2.  Přidat pouze <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.XmlRootAttribute> k třídě, pomocí k tomu explicitně zadat obor názvů pro typ. Provést žádné přidat další atributy z <xref:System.Xml.Serialization> obor názvů řídit, jak se přeložit na XML třídy rozhraní .NET Framework.  
  
 Přijetím tuto metodu, musí mít možnost později provádět třídy rozhraní .NET do kontrakty dat s přidáním systému <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> beze změny výrazně XML, do které se serializují třídy pro přenos. Typy použité ve zprávách webových služeb ASP.NET, bude moct zpracovat jako kontrakty dat podle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, je mezi další výhody lepší výkon v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.  
  
## <a name="security"></a>Zabezpečení  
 Nepoužívejte možnosti ověřování zadané Internetové informační služby (IIS). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]klienti nepodporují je. Pokud služba musí být zabezpečené, pomocí možnosti poskytované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], protože tyto možnosti jsou bohatší a je založený na standardních protokolů.  
  
## <a name="see-also"></a>Viz také  
 [Očekávání přechodu služby Windows Communication Foundation: usnadnění budoucí migrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
