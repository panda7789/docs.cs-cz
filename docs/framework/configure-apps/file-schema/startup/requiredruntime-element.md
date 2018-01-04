---
title: "&lt;requiredRuntime –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 12be2350cb123407b2f71d1f5f07e836ccddb9c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltrequiredruntimegt-element"></a>&lt;requiredRuntime –&gt; – Element
Určuje, jestli aplikace podporuje pouze verzi 1.0 modul common language runtime. Tento element je zastaralá a již by nelze použít. [ `supportedRuntime` ](supportedruntime-element.md) Element by měl být místo toho použít.
  
 \<Konfigurace >  
\<spuštění >  
\<requiredRuntime >  
  
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
|`version`|Nepovinný atribut.<br /><br /> Hodnotu řetězce, který určuje verzi rozhraní .NET Framework, který podporuje tuto aplikaci. Řetězcová hodnota musí odpovídat názvu adresáře najít v kořenovém adresáři instalace rozhraní .NET Framework. Nejsou analyzovat obsah hodnotu řetězce.|  
|`safemode`|Nepovinný atribut.<br /><br /> Určuje, zda kód pro spuštění modulu runtime hledat zjistěte verzi modulu runtime v registru.|  
  
## <a name="safemode-attribute"></a>safemode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Kód spuštění modulu runtime hledá v registru. Jedná se o výchozí hodnotu.|  
|`true`|Kód spuštění modulu runtime nezjišťuje v registru.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`startup`|Obsahuje `<requiredRuntime>` elementu.|  
  
## <a name="remarks"></a>Poznámky  
 Musíte použít aplikace založené na podporu pouze verze 1.0 modulu runtime `<requiredRuntime>` elementu. Musíte použít aplikace vytvořené pomocí verze 1.1 nebo novější modulu runtime `<supportedRuntime>` elementu.  
  
> [!NOTE]
>  Pokud použijete [corbindtoruntimebycfg –](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkce zadat konfigurační soubor, je nutné použít `<requiredRuntime>` element pro všechny verze modulu runtime. `<supportedRuntime>` Element se ignoruje, pokud používáte [corbindtoruntimebycfg –](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
 `version` Řetězec atributu musí odpovídat názvu instalační složku pro určenou verzi rozhraní .NET Framework. Tento řetězec nebyl interpretován. Pokud kód pro spuštění modulu runtime nenajde odpovídající složku, není načítání modulu runtime; kód spuštění zobrazí chybovou zprávu a ukončí.  
  
> [!NOTE]
>  Kód spuštění pro aplikaci, která je hostitelem aplikace Microsoft Internet Explorer ignoruje `<requiredRuntime>` elementu.  
  
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
 [Schéma nastavení spouštění](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > Zadání kterou verzi modulu Runtime pro použití](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)
