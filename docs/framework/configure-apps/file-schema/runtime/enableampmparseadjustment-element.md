---
title: '&lt;EnableAmPmParseAdjustment&gt; – Element'
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b17f521be31fa4082d9418c7dad734e37994bbb5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752816"
---
# <a name="ltenableampmparseadjustmentgt-element"></a>&lt;EnableAmPmParseAdjustment&gt; – Element
Určuje, zda datum a čas analýza metody použít upravenou sadu pravidel analyzovat data řetězce, které obsahují den, měsíc, hodinu a označení dop. / odp.  
  
 \<Konfigurace >  
 \<modul runtime >  
\<EnableAmPmParseAdjustment >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda datum a čas analýza metody používat upravenou sadu pravidel analyzovat data řetězce, které obsahují pouze den, měsíc, hodinu a označení dop. / odp.|  
  
### <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0|Datum a čas analýza metody nepoužívejte upravenou pravidla pro Analýza řetězců data, které obsahují pouze den, měsíc, hodinu a označení dop. / odp.|  
|1|Datum a čas analýza metody použít k analýze datum řetězce, které obsahují pouze den, měsíc, hodinu a označení dop. / odp upravenou pravidla.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 `<EnableAmPmParseAdjustment>` Element řídí, jak tyto metody analyzovat data řetězec, který obsahuje číslem dne a měsíce, za nímž následuje hodinu a označení dop. / odp (například "4/10 6 AM"):  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Žádné jiné vzorce jsou vliv.  
  
 `<EnableAmPmParseAdjustment>` Element nemá žádný vliv <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, a <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> metody.  
  
> [!IMPORTANT]
>  V .NET Core a .NET Native jsou ve výchozím nastavení povolené upravenou dop. / odp analýzy pravidla.  
  
 Pokud není povolena analýza pravidlo úpravy, první číslice řetězce se interpretuje jako hodinu 12 hodin a zbytek řetězci s výjimkou dop. / odp označení je ignorováno. Datum a čas, vrátí metoda analýzy se skládá z aktuální datum a hodinu dne extrahovat z řetězce datum.  
  
 Pokud je povolena analýza pravidlo úpravy, analýza metoda interpretovat dne a měsíce jako náležící do aktuálního roku a interpretovat dobu jako hodinu 12 hodin.  
  
 Následující tabulka ukazuje rozdíly <xref:System.DateTime> hodnotu v případě <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> je metoda použitá k analýze řetězec "" 4/10 6 AM"s `<EnableAmPmParseAdjustment>` elementu `enabled` vlastnost nastavena na hodnotu"0"nebo"1". Předpokládá, že dnešní datum je 5. ledna 2017 a zobrazuje datum, jako kdyby je naformátovaný pomocí řetězce formátu "G" zadanou jazykovou verzi.  
  
|Název jazykové verze|Povolit = "0"|Povolit = "1"|  
|------------------|------------------|------------------|  
|en US|1/5/2017 4:00:00: 00|4/10/2017 6:00:00: 00|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Viz také  
 [\<modul runtime > elementu](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
