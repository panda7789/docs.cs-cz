---
title: '&lt;gcallowverylargeobjects –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 750b0dbc925ec484dd80e1796ba991435e354709
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745224"
---
# <a name="ltgcallowverylargeobjectsgt-element"></a>&lt;gcallowverylargeobjects –&gt; – Element
Na 64bitových platformách povoluje pole, jejichž celková velikost je větší než 2 gigabajty (GB).  
  
 \<Konfigurace > elementu  
\<modul runtime > elementu  
\<gcallowverylargeobjects – > elementu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda jsou pole o celkové velikosti větší než 2 GB povolena na 64bitových platformách.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Pole o celkové velikosti větší než 2 GB nejsou povolena. Toto nastavení je výchozí.|  
|`true`|Pole o celkové velikosti větší než 2 GB jsou povolena na 64bitových platformách.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Použití tohoto prvku v konfiguračním souboru aplikace umožňuje použití polí, která jsou větší než 2 GB, ale nedojde ke změně jiných omezení velikosti objektu nebo velikosti pole:  
  
-   Maximální počet prvků v poli je <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.  
  
-   Maximální index v jakémkoli jednom rozměru je 2 147 483 591 (0x7FFFFFC7) pro bajtová pole a pole jednobajtových struktur a 2 146 435 071 (0X7FEFFFFF) pro ostatní typy.  
  
-   Maximální velikost řetězců a dalších objektů mimo pole se nezmění.  
  
> [!CAUTION]
>  Před zapnutím této funkce je třeba se ujistit, že aplikace neobsahuje nebezpečný kód, což předpokládá, že jsou všechna pole menší než 2 GB. Například nebezpečný kód, který používá pole jako vyrovnávací paměť, může být náchylný k přetečení zásobníku, pokud se při jeho psaní vycházelo z předpokladu, že pole nebude větší než 2 GB.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak tuto funkci pro aplikaci povolit.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
