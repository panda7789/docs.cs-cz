---
title: "Přehled integrace s aplikacemi modelu COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e995fc66a925cb0ebe272c9dceca1ba63b9459d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="integrating-with-com-applications-overview"></a>Přehled integrace s aplikacemi modelu COM
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]bohaté prostředí pro vytváření propojených aplikací poskytuje vývojářům spravovaného kódu. Ale pokud máte významné investice v nespravovaném kódu založené na modelu COM a nechcete, aby k migraci, můžete stále integrovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webové služby přímo do existujícího kódu pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] monikeru služby. Monikeru služby lze použít z celý na základě rozsahu COM vývojových prostředí, například Office VBA, Visual Basic 6.0 nebo Visual C++ verze 6.0.  
  
> [!NOTE]
>  Používá monikeru služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komunikační kanál pro veškerou komunikaci. Mechanismy zabezpečení a identita pro tento kanál se liší od těch, které používá v standardní COM a modelu DCOM proxy. Kromě toho protože používá monikeru služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komunikační kanál výchozího časového limitu je jedna minuta pro všechna volání.  
  
 Monikeru služby se používá s `GetObject` funkce nespravované vývojáře poskytnout přístup silného typu, COM specifické pro volání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webové služby. To vyžaduje, aby definice místní, COM – viditelné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webového kontrakt služby a vazby, který se má použít. Stejně jako jiné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienty, monikeru služby musí vytvořit typové kanál ke službě, i když tento kanál konstrukce transparentně dojde k programátory COM při prvním volání metoda.  
  
 Společné s další [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientů, při použití přezdívka, aplikace zadejte adresy, vazby a smlouvy ke komunikaci se službou. Kontrakt lze zadat v jednom z následujících způsobů:  
  
-   Typové kontrakt – kontrakt je zaregistrován jako typ viditelné modelu COM v klientském počítači.  
  
-   Kontrakt WSDL – kontrakt poskytuje ve formě dokumentu WSDL.  
  
-   Kontrakt MEX – kontrakt se načte v době běhu z koncového bodu metadat Exchange (MEX).  
  
## <a name="parameters-supported-by-the-service-moniker"></a>Parametry nepodporuje Monikeru služby  
 V následující tabulce jsou uvedeny parametry, které jsou podporovány monikeru služby.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`address`|Adresa URL umístění služby.|  
|`binding`|Název oddílu vazby v konfiguraci aplikace.|  
|`bindingConfiguration`|Vazba s názvem instance z v části s názvem vazby.|  
|`contract`|Rozhraní identifikátor (IID), který představuje kontrakt služby nebo název kontraktu (z MEX).|  
|`wsdl`|WSDL dokument, který poskytuje alternativní forma definici kontraktu.|  
|`spnIdentity`|Identita serveru hlavní název (SPN) pro použití ke komunikaci se službou.|  
|`upnIdentity`|Identita hlavní název (UPN) uživatele, které bude použito ke komunikaci se službou.|  
|`dnsIdentity`|Identita DNS, které bude použito ke komunikaci se službou.|  
|`mexAddress`|Umístění URL metadat Exchange (MEX) koncového bodu služby.|  
|`mexBinding`|Z konfigurace aplikace pro připojení ke koncovému bodu MEX vazby název oddílu.|  
|`mexBindingConfiguration`|Vazba s názvem instance z v části s názvem vazby pro připojení ke koncovému bodu MEX.|  
|`bindingNamespace`|Namespace název oddílu vazba z načtené MEX|  
|`contractNamespace`|Namespace kontraktu z načtené MEX|  
|`mexSpnIdentity`|Identity hlavní název (SPN) serveru, které bude použito ke komunikaci s koncovým bodem MEX.|  
|`mexUpnIdentity`|Identita hlavní název (UPN) uživatele, které bude použito ke komunikaci s koncovým bodem MEX.|  
|`mexDnsIdentity`|Identita DNS, které bude použito ke komunikaci s koncovým bodem MEX.|  
|`serializer`|Zadejte buď "xml" nebo "kontraktu" serializátor použití.|  
  
> [!NOTE]
>  I když používají s klienty zcela založená na modelu COM, vyžaduje monikeru služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a podpůrné rozhraní .NET Framework 2.0 k instalaci na klientském počítači. Je také důležité, aby klientských aplikací, které použití monikeru služby načíst příslušnou verzi modulu runtime rozhraní .NET Framework. Při použití monikeru v rámci aplikace Office, může být nutný k zajištění, že je načteno správnou verzi konfiguračního souboru. Například v aplikaci Excel, musí být umístěny následující text v souboru s názvem Excel.exe.config ve stejném adresáři jako soubor Excel.exe:  
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
  
## <a name="see-also"></a>Viz také  
 [Postupy: registrace a konfigurace Monikeru služby](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
