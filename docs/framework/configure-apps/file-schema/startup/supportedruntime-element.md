---
title: "&lt;supportedRuntime&gt; – Element"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4b0967790f2bbf8fa9a889c56fa9c5168f7523bd
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/20/2018
---
# <a name="ltsupportedruntimegt-element"></a>&lt;supportedRuntime&gt; – Element

Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje. Tento prvek by měl být použit všemi aplikacemi sestavenými pomocí rozhraní .NET Framework 1.1 a staršími verzemi.  
  
[\<Konfigurace >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
&nbsp;&nbsp;[\<spuštění >](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**  
  
## <a name="syntax"></a>Syntaxe
  
```xml  
<supportedRuntime version="runtime version" sku="sku id"/>  
```  
  
## <a name="attributes"></a>Atributy
  
|Atribut|Popis|  
|---------------|-----------------|  
|**verze**|Nepovinný atribut.<br /><br /> Hodnota řetězce, která určuje verzi modulu Common Language Runtime (CLR), který aplikace podporuje. Platné hodnoty z `version` atributů najdete v tématu [hodnoty "runtime verze"](#version) části. **Poznámka:** prostřednictvím rozhraní .NET Framework 3.5 "*verzi modulu runtime*" hodnota má podobu *hlavní*. *méně závažné*. *sestavení*. Od verze [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], pouze čísla hlavní verze a podverze jsou vyžadována (tedy "v4.0" místo "v4.0.30319"). Je doporučen kratší řetězec.|  
|**sku**|Nepovinný atribut.<br /><br /> Hodnotu řetězce, který určuje skladové jednotky (SKU), který naopak určuje, jaké verze rozhraní .NET Framework podporuje tuto aplikaci.<br /><br /> Od verze rozhraní .NET Framework 4.0, použití `sku` se doporučuje atribut.  Pokud jsou k dispozici, znamená to verzi rozhraní .NET Framework, že cílem aplikace.<br /><br /> Platné hodnoty atributu, sku, najdete v článku [hodnoty "sku id"](#sku) části.|  
  
## <a name="remarks"></a>Poznámky

Pokud  **\<supportedRuntime >** element není k dispozici v konfiguračním souboru aplikace, je použít verzi modulu runtime použitý k sestavení aplikace.  

**\<SupportedRuntime >** element má být používána všechny aplikace vytvořené pomocí verze 1.1 nebo novější modulu runtime. Musíte použít aplikace založené na podporu pouze verze 1.0 modulu runtime [ \<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element.  
  
> [!NOTE]
>  Pokud použijete [corbindtoruntimebycfg –](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkce zadat konfigurační soubor, je nutné použít `<requiredRuntime>` element pro všechny verze modulu runtime. `<supportedRuntime>` Element se ignoruje, pokud používáte [corbindtoruntimebycfg –](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Pro aplikace, které podporují verze modulu runtime z rozhraní .NET Framework 1.1 až 3.5, když jsou podporovány více verzí modulu runtime, první prvek by měl určovat nejvíc preferovaný verzi modulu runtime a posledním prvkem by měl určovat nejmenší upřednostňované verze. Pro aplikace, které podporují rozhraní .NET Framework 4.0 nebo novější verze `version` atribut uvádí verze CLR, což je obvyklé na rozhraní .NET Framework 4 a novější verze, a `sku` atribut uvádí, jedna verze rozhraní .NET Framework, aplikace cíle.  
  
> [!NOTE]
>  Pokud vaše aplikace používá starší verze aktivace cesty, jako [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), a chcete tyto cesty k aktivaci 4 verzi modulu CLR místo starší verze, nebo pokud je vaše aplikace vytvořené s nástroji [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], ale je závislý na sestavení ve smíšeném režimu vytvořené s dřívější verzi rozhraní .NET Framework není dostačující k určení [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] v seznamu podporovaných moduly runtime. Kromě toho v [ \<spuštění > element](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) v konfiguračním souboru, musíte nastavit `useLegacyV2RuntimeActivationPolicy` atribut `true`. Však nastavení tohoto atributu na `true` znamená, že jsou všechny součásti, které jsou vytvořeny v předchozích verzích rozhraní .NET Framework spustit pomocí [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] místo moduly runtime nebyly vytvořené s nástroji.  
  
Doporučujeme aplikaci otestovat se všemi verzemi .NET Framework, na kterých by měla být spuštěna.  
  
<a name="version"></a>   
## <a name="runtime-version-values"></a>hodnoty "runtime verze"  
`runtime` Atribut určuje verzi Common Language Runtime (CLR), která je nutná k dané aplikaci. Všimněte si, že všechny verze rozhraní .NET Framework v4.x zadejte `v4.0` CLR. Následující tabulka uvádí platné hodnoty pro *verzi modulu runtime* hodnotu `version` atribut.  

|Verze rozhraní .NET Framework|`version`atribut|  
|----------------------------|-------------------------|  
|1.0|"v1.0.3705"|  
|1.1|"v1.1.4322"|  
|2.0|"v2.0.50727"|  
|3.0|"v2.0.50727"|  
|3.5|"v2.0.50727"|  
|4.0-4.7.1|"v4.0"|  

<a name="sku"></a>   
## <a name="sku-id-values"></a>hodnoty "sku id"

`sku` Atribut target framework Přezdívka (TFM) používá k označení verzi rozhraní .NET Framework, který cílí a vyžaduje ke spuštění aplikace. Následující tabulka uvádí platné hodnoty, které jsou podporovány `sku` atribut od verze rozhraní .NET Framework 4.
  
|Verze rozhraní .NET Framework|`sku`atribut|  
|----------------------------|---------------------|  
|4.0|". NETFramework, verze = v4.0 "|  
|4.0, profil klienta|". NETFramework, verze = v4.0, profil = klienta "|  
|4.0, aktualizace platformy 1|.NETFramework,Version=v4.0.1|  
|4.0, profil klienta aktualizací 1|.NETFramework,Version=v4.0.1,Profile=Client|  
|4.0, aktualizace platformy 2|.NETFramework,Version=v4.0.2|  
|4.0, profil klienta aktualizací 2|.NETFramework,Version=v4.0.2,Profile=Client|  
|4.0, aktualizace platformy 3|.NETFramework,Version=v4.0.3|  
|4.0, profil klienta aktualizací 3|.NETFramework,Version=v4.0.3,Profile=Client|  
|4.5|". NETFramework, verze = v4.5 "|  
|4.5.1|". NETFramework, verze = v4.5.1 "|  
|4.5.2|". NETFramework, verze = v4.5.2 "|  
|4.6|". NETFramework, verze = 4.6. "|  
|4.6.1|". NETFramework, verze = v4.6.1 "|  
|4.6.2|". NETFramework, verze = v4.6.2 "|  
|4.7|". NETFramework, verze = v4.7 "|
|4.7.1|". NETFramework, verze = v4.7.1 "|

## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit verzi podporované runtime v konfiguračním souboru. Konfigurační soubor označuje, že aplikace cílí rozhraní .NET Framework 4.7.  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />  
   </startup>  
</configuration>  
```  
  
## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace.

## <a name="see-also"></a>Viz také

 [Schéma nastavení spouštění](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Vnitroprocesové souběžné provádění](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)  
