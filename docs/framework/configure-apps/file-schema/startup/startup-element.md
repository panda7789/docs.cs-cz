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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153725"
---
# <a name="startup-element"></a>\<spouštěcí> prvek

Určuje informace o spuštění běžného jazyka.

[**\<>konfigurace**](../configuration-element.md)  
&nbsp;&nbsp;**\<>pro spuštění**  

## <a name="syntax"></a>Syntaxe

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|Nepovinný atribut.<br /><br /> Určuje, zda má být povolena zásada aktivace za běhu rozhraní .NET Framework 2.0 nebo zda se mají použít zásady aktivace rozhraní .NET Framework 4.|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy, atribut

|Hodnota|Popis|
|-----------|-----------------|
|`true`|Povolte zásady aktivace runtime rozhraní .NET Framework 2.0 pro zvolený běhový čas, kterým je svázání starších technik aktivace runtime (například [funkce CorBindToRuntimeEx)](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)s runtime vybraným z konfiguračního souboru namísto jejich omezení pomocí clr verze 2.0. Pokud je tedy z konfiguračního souboru vybrána verze CLR verze 4 nebo novější, jsou sestavení v kombinovaném režimu vytvořená s dřívějšími verzemi rozhraní .NET Framework načtena s vybranou verzí CLR. Nastavení této hodnoty zabrání clr verze 1.1 nebo CLR verze 2.0 z načtení do stejného procesu, účinně zakázání funkce v procesu side-by-side.|
|`false`|Použijte výchozí zásady aktivace pro rozhraní .NET Framework 4 a novější, což je umožnit starší mandatorní aktivační techniky pro načtení CLR verze 1.1 nebo 2.0 do procesu. Nastavení této hodnoty zabrání načtení sestavení v smíšeném režimu do rozhraní .NET Framework 4 nebo novější, pokud nebyly vytvořeny s rozhraním .NET Framework 4 nebo novějším. Tato hodnota je výchozí.|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[\<požadovaná>běhu](requiredruntime-element.md)|Určuje, že aplikace podporuje pouze verzi 1.0 běžného jazykového běhu. Aplikace vytvořené s runtime verze 1.1 nebo novější by měl y použít ** \<supportedRuntime>** element.|
|[\<podporované>modulu Runtime](supportedruntime-element.md)|Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|

## <a name="remarks"></a>Poznámky

 Prvek ** \<supportedRuntime>** by měl být používán všemi aplikacemi vytvořenými pomocí verze 1.1 nebo novější modulu runtime. Aplikace vytvořené pro podporu pouze verze 1.0 runtime musí používat ** \<prvek requiredRuntime>.**

 Spouštěcí kód aplikace hostované v aplikaci Microsoft Internet Explorer ignoruje ** \<spouštěcí>** prvek a jeho podřízené prvky.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>Atribut useLegacyV2RuntimeActivationPolicy

 Tento atribut je užitečný, pokud vaše aplikace používá starší aktivační cesty, jako je například [funkce CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), a chcete, aby tyto cesty aktivovaly verzi 4 CLR namísto starší verze, nebo pokud je aplikace vytvořena s rozhraním .NET Framework 4, ale má závislost na sestavení ve smíšeném režimu vytvořeném se starší verzí rozhraní .NET Framework. V těchto scénářích nastavte `true`atribut .

> [!NOTE]
> Nastavení atributu `true` zabránit CLR verze 1.1 nebo CLR verze 2.0 z načtení do stejného procesu, účinně zakázání v procesu side-by-side funkce (viz [Side-by-Side provedení pro COM Interop).](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak zadat verzi runtime v konfiguračním souboru.

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
- [Postup: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novějších verzí](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Souběžné provádění pro kominterop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [Vnitroprocesové souběžné provádění](../../../deployment/in-process-side-by-side-execution.md)
