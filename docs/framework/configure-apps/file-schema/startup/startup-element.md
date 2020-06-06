---
title: <startup> – element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153725"
---
# <a name="startup-element"></a>\<startup> – element

Určuje informace o spuštění společného jazykového modulu runtime.

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a>Syntaxe

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|Nepovinný atribut.<br /><br /> Určuje, jestli se má povolit zásada aktivace modulu runtime .NET Framework 2,0 nebo jestli se mají používat zásady aktivace .NET Framework 4.|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy – atribut

|Hodnota|Description|
|-----------|-----------------|
|`true`|Povolte Zásady aktivace modulu runtime .NET Framework 2,0 pro zvolený modul runtime, který je vázán na modul runtime, který se vybere z konfiguračního souboru, namísto [capping na CLR](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)verze 2,0. Proto pokud je CLR verze 4 nebo novější zvolen z konfiguračního souboru, jsou sestavení se smíšeným režimem vytvořená se staršími verzemi .NET Framework načtena se zvolenou verzí modulu CLR. Nastavením této hodnoty zabráníte načtení CLR verze 1,1 nebo CLR verze 2,0 do stejného procesu a efektivně tak zakážete souběžnou funkci v rámci procesu.|
|`false`|Použijte výchozí zásady aktivace pro .NET Framework 4 a novější, což znamená, že je možné do procesu načíst modul CLR verze 1,1 nebo 2,0. Nastavení této hodnoty zabrání načtení sestavení se smíšeným režimem do .NET Framework 4 nebo novějším, pokud se nevytvořila s .NET Framework 4 nebo novějším. Tato hodnota je výchozí.|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Description|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|Určuje, že aplikace podporuje pouze verzi 1,0 modulu CLR (Common Language Runtime). Aplikace sestavené s modulem runtime verze 1,1 nebo novější by měly používat **\<supportedRuntime>** element.|
|[\<supportedRuntime>](supportedruntime-element.md)|Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.|

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Description|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|

## <a name="remarks"></a>Poznámky

 **\<supportedRuntime>** Element by měl být použit všemi aplikacemi sestavenými pomocí verze 1,1 nebo novější. Aplikace sestavené pro podporu pouze verze 1,0 modulu runtime musí používat **\<requiredRuntime>** element.

 Spouštěcí kód pro aplikaci hostovanou v aplikaci Microsoft Internet Explorer ignoruje **\<startup>** prvek a jeho podřízené prvky.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>Atribut useLegacyV2RuntimeActivationPolicy

 Tento atribut je užitečný, pokud vaše aplikace používá starší aktivační cesty, jako je [funkce CorBindToRuntimeEx –](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), a chcete, aby tyto cesty aktivovaly verzi 4 CLR namísto dřívější verze, nebo pokud je vaše aplikace sestavená s .NET Framework 4, ale má závislost na sestavení se smíšeným režimem sestaveným pomocí dřívější verze .NET Framework. V těchto scénářích nastavte atribut na `true` .

> [!NOTE]
> Nastavením atributu `true` zabráníte, aby CLR verze 1,1 nebo CLR verze 2,0 z načtení do stejného procesu, čímž efektivně zakážete souběžnou funkci v rámci procesu (viz [Souběžné spouštění pro zprostředkovatele komunikace s objekty COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>Viz také

- [Schéma nastavení spouštění](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Souběžné spouštění pro zprostředkovatele komunikace s objekty COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [Vnitroprocesové souběžné provádění](../../../deployment/in-process-side-by-side-execution.md)
