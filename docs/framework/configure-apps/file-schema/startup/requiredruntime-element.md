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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697489"
---
# <a name="requiredruntime-element"></a>@no__t – element > 0requiredRuntime

Určuje, že aplikace podporuje pouze verzi 1,0 modulu CLR (Common Language Runtime). Tento prvek je zastaralý a neměl by se už používat. Místo toho by se měl použít prvek [`supportedRuntime`](supportedruntime-element.md) .

[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<startup >** ](startup-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requiredRuntime >**  

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

|Hodnota|Popis|
|-----------|-----------------|
|`false`|Spouštěcí kód modulu runtime vyhledá v registru. Jedná se o výchozí hodnotu.|
|`true`|Spouštěcí kód modulu runtime nevypadá v registru.|

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`startup`|Obsahuje prvek `<requiredRuntime>`.|

## <a name="remarks"></a>Poznámky
 Aplikace sestavené pro podporu pouze verze 1,0 modulu runtime musí používat prvek `<requiredRuntime>`. Aplikace sestavené pomocí verze 1,1 nebo novější v modulu runtime musí používat prvek `<supportedRuntime>`.

> [!NOTE]
> Použijete-li funkci [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) k určení konfiguračního souboru, je nutné použít prvek `<requiredRuntime>` pro všechny verze modulu runtime. Element `<supportedRuntime>` se při použití [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)ignoruje.

 Řetězec atributu `version` se musí shodovat s názvem instalační složky pro zadanou verzi .NET Framework. Tento řetězec není interpretován. Pokud spouštěcí kód modulu runtime nenajde shodnou složku, modul runtime není načten. spouštěcí kód ukazuje chybovou zprávu a ukončí se.

> [!NOTE]
> Spouštěcí kód pro aplikaci, která je hostována v aplikaci Microsoft Internet Explorer, ignoruje prvek `<requiredRuntime>`.

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
- [Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
