---
title: Přehled integrace s aplikacemi modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 6e6ff29e7d292a291c2cb4984a80c5a0927f18d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934968"
---
# <a name="integrating-with-com-applications-overview"></a>Přehled integrace s aplikacemi modelu COM
Windows Communication Foundation (WCF) poskytuje vývojářům spravovaného kódu prostředí s bohatým prostředím pro vytváření připojených aplikací. Nicméně pokud máte významnou investici do nespravovaného kódu založeného na modelu COM a nechcete migrovat, můžete i nadále integrovat webové služby WCF přímo do stávajícího kódu pomocí monikeru služby WCF. Moniker služby lze použít z široké škály vývojových prostředí založených na modelu COM, jako je například Office VBA, Visual Basic 6,0 nebo Visual C++ 6,0.  
  
> [!NOTE]
> Moniker služby používá komunikační kanál WCF pro veškerou komunikaci. Mechanismy zabezpečení a identity pro tento kanál se liší od těch, které se používají ve standardních proxy serverech COM a DCOM. Kromě toho, protože moniker služby používá komunikační kanál WCF, je výchozí časový limit jedna minuta pro všechna volání.  
  
 Moniker služby se používá spolu s `GetObject` funkcí k poskytnutí nespravovaného vývojáře se silným typem, který je specifický pro rozhraní COM pro volání webových služeb WCF. To vyžaduje místní definici kontraktu webové služby WCF, která je viditelná v modelu COM, a vazbu, která se má použít. Podobně jako ostatní klienti WCF musí moniker služby pro službu vytvořit typový kanál, i když se tato konstrukce kanálu transparentně nacházela programátorům COM při prvním volání metody.  
  
 V běžných případech s jinými klienty WCF při použití monikeru aplikace určují adresu, vazbu a kontrakt ke komunikaci se službou. Kontrakt lze zadat jedním z následujících způsobů:  
  
- Typ kontraktu – kontrakt se na klientském počítači zaregistruje jako viditelný typ modelu COM.  
  
- Smlouva WSDL – smlouva je dodávána ve formě dokumentu WSDL.  
  
- Služba MEX – kontrakt se načítá za běhu z koncového bodu výměny metadat (MEX).  
  
## <a name="parameters-supported-by-the-service-moniker"></a>Parametry podporované Monikerem služby  
 V následující tabulce jsou uvedeny parametry, které jsou podporovány monikerem služby.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`address`|Umístění adresy URL služby.|  
|`binding`|Název oddílu vazby z konfigurace aplikace.|  
|`bindingConfiguration`|Pojmenovaná instance vazby v rámci pojmenované vazby oddílu.|  
|`contract`|Identifikátor rozhraní (IID), který představuje kontrakt služby nebo název kontraktu (ze MEX).|  
|`wsdl`|Dokument WSDL, který poskytuje alternativní formu definice smlouvy.|  
|`spnIdentity`|Identita hlavního názvu serveru (SPN), která se má použít ke komunikaci se službou.|  
|`upnIdentity`|Identita hlavního názvu uživatele (UPN), která se má použít ke komunikaci se službou.|  
|`dnsIdentity`|Identita DNS, která se má použít ke komunikaci se službou.|  
|`mexAddress`|Umístění adresy URL koncového bodu výměny metadat (MEX) služby.|  
|`mexBinding`|Název oddílu vazby z konfigurace aplikace pro připojení ke koncovému bodu MEX.|  
|`mexBindingConfiguration`|Pojmenovaná instance vazby z pojmenovaného oddílu vazby pro připojení ke koncovému bodu MEX.|  
|`bindingNamespace`|Obor názvů názvu oddílu vazby z načteného MEX|  
|`contractNamespace`|Obor názvů kontraktu z načteného MEX|  
|`mexSpnIdentity`|Identita hlavního názvu serveru (SPN), která se má použít ke komunikaci s koncovým bodem MEX.|  
|`mexUpnIdentity`|Identita hlavního názvu uživatele (UPN), která se má použít ke komunikaci s koncovým bodem MEX.|  
|`mexDnsIdentity`|Identita DNS, která se má použít ke komunikaci s koncovým bodem MEX.|  
|`serializer`|Zadejte použití serializátoru "XML" nebo "DataContract".|  
  
> [!NOTE]
> I v případě, že se používá výhradně u klientů založených na modelu COM, moniker služby vyžaduje službu WCF a podporu .NET Framework 2,0 pro instalaci do klientského počítače. Je také důležité, aby klientské aplikace, které používají moniker služby, načetly příslušnou verzi .NET Framework runtime. Při použití monikeru v aplikacích Office může být vyžadován konfigurační soubor, aby bylo zajištěno, že bude načtena správná verze rozhraní. Například v aplikaci Excel by měl být následující text umístěn do souboru s názvem Excel. exe. config ve stejném adresáři jako soubor aplikace Excel. exe:  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Registrace a konfigurace monikeru služby](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
