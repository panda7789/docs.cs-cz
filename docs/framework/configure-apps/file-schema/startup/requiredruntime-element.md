---
title: <requiredRuntime> – element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697489"
---
# <a name="requiredruntime-element"></a>\<requiredRuntime> – element

Určuje, že aplikace podporuje pouze verzi 1,0 modulu CLR (Common Language Runtime). Tento prvek je zastaralý a neměl by se už používat. [`supportedRuntime`](supportedruntime-element.md)Místo toho by se měl použít element.

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a>Syntaxe

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`version`|Nepovinný atribut.<br /><br /> Řetězcová hodnota, která určuje verzi .NET Framework, kterou tato aplikace podporuje. Hodnota řetězce se musí shodovat s názvem adresáře, který se nachází v kořenovém adresáři instalace .NET Framework. Obsah řetězcové hodnoty není analyzován.|
|`safemode`|Nepovinný atribut.<br /><br /> Určuje, zda běhový kód spuštění vyhledá v registru, aby bylo možné zjistit verzi modulu runtime.|

## <a name="safemode-attribute"></a>safemode – atribut

|Hodnota|Description|
|-----------|-----------------|
|`false`|Spouštěcí kód modulu runtime vyhledá v registru. Toto je výchozí hodnota.|
|`true`|Spouštěcí kód modulu runtime nevypadá v registru.|

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Description|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`startup`|Obsahuje `<requiredRuntime>` element.|

## <a name="remarks"></a>Poznámky
 Aplikace sestavené pro podporu pouze verze 1,0 modulu runtime musí používat `<requiredRuntime>` element. Aplikace sestavené pomocí verze 1,1 nebo novější v modulu runtime musí používat `<supportedRuntime>` element.

> [!NOTE]
> Použijete-li funkci [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) k určení konfiguračního souboru, je nutné použít `<requiredRuntime>` element pro všechny verze modulu runtime. `<supportedRuntime>`Element je ignorován při použití [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).

 `version`Řetězec atributu musí odpovídat názvu instalační složky pro zadanou verzi .NET Framework. Tento řetězec není interpretován. Pokud spouštěcí kód modulu runtime nenajde shodnou složku, modul runtime není načten. spouštěcí kód ukazuje chybovou zprávu a ukončí se.

> [!NOTE]
> Spouštěcí kód pro aplikaci, která je hostována v aplikaci Microsoft Internet Explorer, ignoruje `<requiredRuntime>` prvek.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>Viz také

- [Schéma nastavení spouštění](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
