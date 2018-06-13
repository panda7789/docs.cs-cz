---
title: '&lt;Netfx45_cultureawarecomparergethashcode_longstrings –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41fc4bc7a6a10a6f99752112f951b66f80d493fe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754181"
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a>&lt;Netfx45_cultureawarecomparergethashcode_longstrings –&gt; – Element
Určuje, zda modul runtime používá k výpočtu kódů hash pro pevné velikosti paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metoda.  
  
 \<Konfigurace >  
\<modul runtime >  
< netfx45_cultureawarecomparergethashcode_longstrings – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul Common Language Runtime (CLR) přidělí při výpočtu kódů hash pevnou velikost paměti.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0|Modul common language runtime přiděluje proměnné množství paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash. Toto nastavení je výchozí.|  
|1|Modul common language runtime přiděluje pevné velikosti paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení modul common language runtime přiděluje proměnné množství paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody a <xref:System.ArgumentException> může být vyvolána, když se metoda pokusí výpočtu hash velké řetězců (přes několik mil. znaků). Přidáním tohoto prvku do konfiguračního souboru aplikace a nastavení jeho `enabled` atributu na hodnotu "1", můžete určit, že <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu používají alternativní algoritmus, který přiděluje pevné velikosti paměti pro výpočet kódů hash.  
  
> [!IMPORTANT]
>  `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Element není používáno ve [!INCLUDE[win8](../../../../../includes/win8-md.md)] a novějších verzích.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
