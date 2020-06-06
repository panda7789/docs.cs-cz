---
title: <add> z <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850328"
---
# <a name="add-of-serviceactivations"></a>\<add> z \<serviceActivations>

Prvek konfigurace, který umožňuje definovat nastavení aktivace virtuální služby, která se mapují na typy služeb Windows Communication Foundation (WCF). Díky tomu je možné aktivovat služby hostované v rámci služby/IIS bez souboru. svc.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

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
|instalací|Řetězec, který určuje název typu CLR továrny, která generuje prvek aktivace služby.|
|služba|ServiceType, který implementuje službu (buď plně kvalifikovaný typeName, nebo krátký TypeName (při umístění do složky App_Code).|
|Adresa relativeAddress|Relativní adresa v rámci aktuální aplikace služby IIS – například "Service. svc". V WCF 4,0 tato relativní adresa musí obsahovat jednu ze známých přípon souborů (. svc,. xamlx,...). Neexistuje žádný fyzický soubor pro relativeUrl.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Konfigurační oddíl, který popisuje nastavení aktivace.|

## <a name="remarks"></a>Poznámky

Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru Web. config.

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

Pomocí této konfigurace můžete aktivovat GreetingService bez použití souboru. svc.

Všimněte si, že `<serviceHostingEnvironment>` je konfigurace na úrovni aplikace. Je nutné umístit `web.config` konfiguraci obsahující konfiguraci do kořenového adresáře virtuální aplikace. Kromě toho `serviceHostingEnvironment` je machineToApplication dědičná část. Pokud v kořenovém adresáři počítače zaregistrujete jednu službu, bude tato služba dědit všechny služby v aplikaci.

Aktivace založená na konfiguraci podporuje aktivaci prostřednictvím protokolu HTTP i jiného typu než HTTP. Vyžaduje rozšíření v adresa relativeAddress, tj.. svc,. XOML nebo. xamlx. Můžete namapovat vlastní rozšíření na know buildProviders, které vám pak umožní aktivovat službu přes jakékoli rozšíření. Po konfliktu `<serviceActivations>` oddíl přepíše registraci. svc.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
