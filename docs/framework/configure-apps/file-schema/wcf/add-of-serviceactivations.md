---
title: <add> z <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 2a3ba6d41059a480fe610254c0407df16d149e3b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673038"
---
# <a name="add-of-serviceactivations"></a>\<add> of \<serviceActivations>

Konfigurace element, který umožňuje definování nastavení aktivace virtuální služby, která je namapována na daný typ služby Windows Communication Foundation (WCF). To umožňuje aktivovat službám hostovaným ve WAS / IIS bez souboru .svc.

\<system.ServiceModel>\
\<serviceHostingEnvironment>

## <a name="syntax"></a>Syntaxe

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|objekt pro vytváření|Řetězec určující název typu CLR továrny, která generuje prvek aktivace služby.|
|service|ServiceType, který implementuje služby (úplný kvalifikovaný název typu nebo krátké Typename (Pokud je umístěn ve složce App_Code).|
|relativeAddress|Relativní adresu v rámci aktuální aplikace služby IIS – například "Service.svc". V WCF 4.0 tato relativní adresa musí obsahovat jeden přípon souborů známých (.svc .xamlx,...). Žádný fyzický soubor musí být pro relativeUrl|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Konfigurační oddíl, který popisuje nastavení aktivace.|

## <a name="remarks"></a>Poznámky

Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru web.config.

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

Pomocí této konfigurace, můžete aktivovat GreetingService bez použití souboru .svc.

Všimněte si, že `<serviceHostingEnvironment>` je konfigurace na úrovni aplikace. Je nutné umístit `web.config` obsahující konfiguraci v kořenu virtuální aplikace. Kromě toho `serviceHostingEnvironment` machineToApplication odvoditelný oddíl. Když si zaregistrujete jedinou službou v kořenové složce na počítači, každá služba aplikace zdědí tuto službu.

Aktivace podle konfigurace podporuje aktivaci přes protokol http a jiným protokolem než http. Vyžaduje adresu relativeAddress, tj. .svc, XOML nebo .xamlx s rozšířeními. Vlastní rozšíření můžete namapovat buildProviders ví, která vám pak umožní k aktivaci služby přes jakékoli rozšíření. Při konfliktu `<serviceActivations>` části přepíše .svc registrace.

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
