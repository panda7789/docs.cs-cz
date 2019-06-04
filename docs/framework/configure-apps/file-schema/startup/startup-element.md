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
ms.openlocfilehash: 5b15c504a01a0ab8e17b8ad8811d9ed183609322
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456274"
---
# <a name="startup-element"></a>\<Po spuštění > – element

Určuje informace o spuštění modulu runtime jazyka common.

 \<configuration> \<startup>

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
|`useLegacyV2RuntimeActivationPolicy`|Nepovinný atribut.<br /><br /> Určuje, jestli se má povolit [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] Zásady aktivace modulu runtime, nebo použít [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] Zásady aktivace.|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>atribut useLegacyV2RuntimeActivationPolicy

|Value|Popis|
|-----------|-----------------|
|`true`|Povolit [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] Zásady aktivace modulu runtime pro zvolený runtime, která je k vytvoření vazby techniky aktivace starší verzi modulu runtime (například [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) do modulu runtime, zvolit z konfiguračního souboru místo omezení je v modulu CLR verze 2.0. Proto pokud je zvolená verze modulu CLR 4 nebo novější z konfiguračního souboru, sestavení ve smíšeném režimu vytvořených v dřívějších verzích rozhraní .NET Framework jsou načtené na zvolené verzi CLR. Pokud tuto hodnotu nastavíte brání CLR verze 1.1 nebo CLR verze 2.0 načtení do stejného procesu efektivně zákaz funkce vnitroprocesové vedle sebe.|
|`false`|Pomocí aktivace výchozí zásady pro rozhraní .NET Framework 4 a novější, což je povolit starší modul runtime techniky aktivace pro načtení modulu CLR verze 1.1 nebo 2.0 do procesu. Nastavení této hodnoty brání ve smíšeném režimu sestavení z načítání do rozhraní .NET Framework 4 nebo novější, není-li, kterými byly vytvořeny pomocí rozhraní .NET Framework 4 nebo novější. Tato hodnota je výchozí hodnota.|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[\<requiredRuntime >](requiredruntime-element.md)|Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime. Používejte aplikace sestavené s modulem runtime verze 1.1 nebo vyšší  **\<supportedRuntime >** elementu.|
|[\<supportedRuntime >](supportedruntime-element.md)|Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.|

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|

## <a name="remarks"></a>Poznámky

 **\<SupportedRuntime >** element by měl být použit všemi aplikacemi sestavenými pomocí verze 1.1 nebo novější modul runtime. Aplikace sestavené s podporou pouze verze 1.0 modulu runtime musí použít  **\<requiredRuntime >** elementu.

 Ignoruje při spuštění kódu pro aplikace hostované v aplikaci Internet Explorer  **\<spuštění >** elementu a jeho podřízené prvky.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>Atribut useLegacyV2RuntimeActivationPolicy

 Tento atribut je užitečné, pokud vaše aplikace používá starší verzi aktivační cesty, jako [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), a chcete, aby tyto cesty k aktivaci místo starší verzi modulu CLR verze 4 nebo pokud je vaše aplikace sestavován rozhraní .NET Framework 4, ale obsahuje závislost na sestavení ve smíšeném režimu, vytvořené ve starší verzi rozhraní .NET Framework. V těchto scénářích, nastavte atribut na `true`.

> [!NOTE]
> Nastavením atributu na `true` brání načtení do stejného procesu efektivně zákaz funkce vedle sebe v procesu CLR verze 1.1 nebo CLR verze 2.0 (viz [spuštění vedle sebe pro spolupráci s COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).

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

## <a name="see-also"></a>Viz také:

- [Schéma nastavení spouštění](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Spuštění vedle sebe pro zprostředkovatele komunikace s objekty COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [Vnitroprocesové souběžné provádění](../../../deployment/in-process-side-by-side-execution.md)
