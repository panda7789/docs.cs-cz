---
title: '&lt;Timespan_legacyformatmode –&gt; – Element'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0faf2876680ef5ec3fc7373cae9f81eb091f47a1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="lttimespanlegacyformatmodegt-element"></a>&lt;Timespan_legacyformatmode –&gt; – Element
Určuje, zda modul runtime zachovává starší verze chování při formátování operací s <xref:System.TimeSpan?displayProperty=nameWithType> hodnoty.  
  
 \<Konfigurace >  
\<modul runtime >  
< timespan_legacyformatmode – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime používá starší verze formátování chování s <xref:System.TimeSpan?displayProperty=nameWithType> hodnoty.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Modul runtime neobnoví starší verze formátování chování.|  
|`true`|Modul runtime obnoví starší verze formátování chování.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], <xref:System.TimeSpan?displayProperty=nameWithType> struktury implementuje <xref:System.IFormattable> rozhraní a podporuje formátování operace s řetězci standardní a vlastní formát. Pokud metoda analýzy zaznamená řetězce formátu nebo nepodporovaný formát specifikátor, vyvolá výjimku <xref:System.FormatException>.  
  
 V předchozích verzích rozhraní .NET Framework <xref:System.TimeSpan> struktura neimplementovala <xref:System.IFormattable> a nepodporoval řetězce formátu. Ale celá řada vývojářů omylem předpokládá se, že <xref:System.TimeSpan> podporovat sadu řetězce formátu a použít je v [složené formátování operations](../../../../../docs/standard/base-types/composite-formatting.md) s metodami, jako <xref:System.String.Format%2A?displayProperty=nameWithType>. Normálně Pokud typ implementuje <xref:System.IFormattable> a podporuje formátování řetězce, volání metodě formátování s nepodporovaný formát řetězce obvykle throw <xref:System.FormatException>. Ale protože <xref:System.TimeSpan> neimplementovala <xref:System.IFormattable>, modul runtime ignorovat řetězec formátu a místo toho volat <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metoda. To znamená, že i když řetězce formátu nemělo žádný vliv na operace formátování, jejich přítomnosti nevedly <xref:System.FormatException>.  
  
 Pro případy, ve kterých starší kód předá složeného formátování metoda a neplatný formát řetězce a tento kód nemůže být překompilovat, můžete použít `<TimeSpan_LegacyFormatMode>` elementu, který chcete obnovit starší verze <xref:System.TimeSpan> chování. Když nastavíte `enabled` tohoto prvku do atribut `true`, složené formátování metoda výsledkem volání <xref:System.TimeSpan.ToString?displayProperty=nameWithType> místo <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>a <xref:System.FormatException> není vyvolána.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.TimeSpan> objekt a pokusy o naformátujte ho s <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> metoda pomocí Nepodporovaný standardní formát řetězce.  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 Při spuštění v příkladu [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] nebo ve starší verzi, zobrazí se následující výstup:  
  
```  
12:30:45  
```  
  
 To zřetelně liší z výstupu Pokud spustíte v příkladu [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] nebo novější verze:  
  
```  
Invalid Format  
```  
  
 Ale pokud přidáte následujícího konfiguračního souboru v příkladu je adresáře a spusťte v příkladu [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] nebo novější verze je stejná jako vyprodukované v příkladu, když se spustí na výstup [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
