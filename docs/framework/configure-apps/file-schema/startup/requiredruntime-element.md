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
ms.openlocfilehash: 5e528a8b81fa3d9abc4f345d18f01e33f483a4a9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254727"
---
# <a name="requiredruntime-element"></a>\<requiredRuntime > – element

Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime. Tento element je zastaralá a již by nelze použít. [ `supportedRuntime` ](supportedruntime-element.md) Element by měl místo toho použít.

\<configuration> \<startup> \<requiredRuntime>

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
|`version`|Nepovinný atribut.<br /><br /> Řetězcovou hodnotu, která určuje verzi rozhraní .NET Framework, která podporuje tuto aplikaci. Řetězcová hodnota musí odpovídat názvu adresáře v kořenu instalace rozhraní .NET Framework. Nejsou analyzovat obsah řetězcovou hodnotu.|
|`safemode`|Nepovinný atribut.<br /><br /> Určuje, zda modul runtime spouštěcí kód vyhledá z registru zjistit verzi modulu runtime.|

## <a name="safemode-attribute"></a>safemode – atribut

|Hodnota|Popis|
|-----------|-----------------|
|`false`|Spouštěcí kód modulu runtime hledá v registru. Jedná se o výchozí hodnotu.|
|`true`|Spouštěcí kód modulu runtime nezjišťuje v registru.|

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`startup`|Obsahuje `<requiredRuntime>` elementu.|

## <a name="remarks"></a>Poznámky
 Aplikace sestavené s podporou pouze verze 1.0 modulu runtime musí použít `<requiredRuntime>` elementu. Aplikace vytvořené pomocí verze 1.1 nebo novější modul runtime musí použít `<supportedRuntime>` elementu.

> [!NOTE]
> Pokud používáte [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkce zadejte konfigurační soubor, je nutné použít `<requiredRuntime>` – element pro všechny verze modulu runtime. `<supportedRuntime>` Prvek je ignorován při použití [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).

 `version` Atribut řetězců musí odpovídat názvu instalační složku pro zadaná verze rozhraní .NET Framework. Tento řetězec nebyl interpretován. Pokud kód při spuštění modulu runtime nelze najít odpovídající složky, modul runtime není načten. spouštěcí kód zobrazí chybovou zprávu a ukončí.

> [!NOTE]
> Ignoruje spouštěcí kód aplikace, která je hostována v aplikaci Internet Explorer `<requiredRuntime>` elementu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Schéma nastavení spouštění](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)