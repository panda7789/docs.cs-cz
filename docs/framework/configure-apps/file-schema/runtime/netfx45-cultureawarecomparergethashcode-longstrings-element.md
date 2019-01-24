---
title: '&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; Element'
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67dae26733527a85f4fc13734da896193e53db8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576886"
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a>&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; Element
Určuje, zda modul runtime používá pro výpočet kódů hash pro pevnou velikost paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.  
  
 \<Konfigurace >  
\<modul runtime >  
<NetFx45_CultureAwareComparerGetHashCode_LongStrings>  
  
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
|0|Modul common language runtime přiděluje variabilní velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash. Toto nastavení je výchozí.|  
|1|Modul CLR přidělí pevnou velikost paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, modul common language runtime přiděluje variabilní velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody a <xref:System.ArgumentException> může být vyvolána, když se metoda se pokusí výpočtu kódů hash velmi dlouhých řetězců (přes několik milion znaků). Přidáním tohoto prvku do konfiguračního souboru aplikace a nastavení jeho `enabled` atribut na hodnotu "1", můžete určit, že <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metoda použila alternativní algoritmus, který pro výpočet kódů hash přidělí pevnou velikost paměti.  
  
> [!IMPORTANT]
>  `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Není použit element v [!INCLUDE[win8](../../../../../includes/win8-md.md)] a novějších verzích.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
