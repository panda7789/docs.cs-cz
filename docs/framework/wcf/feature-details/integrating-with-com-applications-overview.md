---
title: Přehled integrace s aplikacemi modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 2be428f0ae83596a4398fc9830af40d05f6ab191
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638656"
---
# <a name="integrating-with-com-applications-overview"></a>Přehled integrace s aplikacemi modelu COM
Windows Communication Foundation (WCF) poskytuje vývojářům spravovaného kódu s bohaté prostředí pro vytváření propojených aplikací. Nicméně pokud máte značné investice v nespravovaném kódu na základě modelu COM a nechcete, aby k migraci, můžete stále integrovat webových služeb WCF přímo do vašeho existujícího kódu pomocí monikeru služby WCF. Moniker služby je možné z široký rozsah COM vývoj prostředí, jako je například Office VBA, Visual Basic 6.0 nebo Visual C++ 6.0.  
  
> [!NOTE]
>  Moniker služby používá komunikační kanál WCF pro veškerou komunikaci. Mechanismy zabezpečení a identity pro tento kanál se liší od těch, které ve standardní proxy modelu COM a DCOM používá. Navíc vzhledem k tomu monikeru služby používá komunikační kanál WCF výchozího časového limitu je jedna minuta pro všechna volání.  
  
 Moniker služby se používá s `GetObject` funkce nespravované developer poskytnout přístup silného typu, COM specifické pro volání webových služeb WCF. Tento postup vyžaduje místní, viditelný modulem COM definici kontraktu služby WCF Web a vazbu, která se má použít. Stejně jako ostatní klienti WCF monikeru služby nezbytné vytvořit zadaný kanál ke službě, i když dojde k vytváření tohoto kanálu transparentně na programátorovi modelu COM, při prvním volání metody.  
  
 Společné s ostatními WCF klienty, při použití monikeru zadejte aplikace, adresa, vazba a kontrakt ke komunikaci se službou. Kontrakt lze zadat v jednom z následujících způsobů:  
  
- Typu kontraktu – smlouvy je zaregistrovaný jako typ viditelné modelu COM v klientském počítači.  
  
- Smlouva WSDL – smlouvy se dodává ve formě dokument WSDL.  
  
- Smlouva MEX – smlouvy je načten v době běhu z koncového bodu metadat Exchange (MEX).  
  
## <a name="parameters-supported-by-the-service-moniker"></a>Parametry nepodporuje Monikeru služby  
 V následující tabulce jsou uvedeny parametry, které jsou podporovány monikeru služby.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`address`|Adresa URL umístění služby.|  
|`binding`|Název oddílu vazby z konfigurace aplikace.|  
|`bindingConfiguration`|Instance s názvem vazby z v rámci oddílu s názvem vazby.|  
|`contract`|Identifikátor rozhraní (IID), která představuje kontraktu služby nebo název kontraktu (ze MEX).|  
|`wsdl`|Dokument WSDL, který poskytuje alternativní formy definici kontraktu.|  
|`spnIdentity`|Identita serveru hlavní název (SPN) který se má použít ke komunikaci se službou.|  
|`upnIdentity`|Hlavní název (UPN) identity uživatele se použije ke komunikaci se službou.|  
|`dnsIdentity`|Identitu DNS, který se má použít ke komunikaci se službou.|  
|`mexAddress`|Adresa URL umístění metadat Exchange (MEX) koncového bodu služby.|  
|`mexBinding`|Název oddílu vazby z konfigurace aplikace pro připojení ke koncovému bodu MEX.|  
|`mexBindingConfiguration`|Instance s názvem vazby z v rámci oddílu s názvem vazby pro připojení ke koncovému bodu MEX.|  
|`bindingNamespace`|Namespace názvu oddílu vazby z načtené MEX|  
|`contractNamespace`|Namespace kontraktu v MEX načtené|  
|`mexSpnIdentity`|Identita serveru hlavní název (SPN) který se má použít ke komunikaci s koncovým bodem MEX.|  
|`mexUpnIdentity`|Hlavní název (UPN) identity uživatele se použije ke komunikaci s koncovým bodem MEX.|  
|`mexDnsIdentity`|Identitu DNS, který se má použít ke komunikaci s koncovým bodem MEX.|  
|`serializer`|Vyžaduje použití aplikace "xml" nebo "kontraktu dat datacontract" serializátor.|  
  
> [!NOTE]
>  I když používají klienti zcela založená na modelu COM, vyžaduje monikeru služby WCF a podpory .NET Framework 2.0 nainstalované v klientském počítači. Je velmi důležité, aby klientské aplikace, které použití monikeru služby načíst příslušnou verzi modulu runtime rozhraní .NET Framework. Při použití monikeru v rámci aplikace Office, může být nutný k zajištění, že je načtena správná framework verze konfiguračního souboru. Například s Excelem, následující text by měl umístit do souboru s názvem Excel.exe.config ve stejném adresáři jako soubor Excel.exe:  
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

- [Postupy: Registrace a konfigurace Monikeru služby](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
