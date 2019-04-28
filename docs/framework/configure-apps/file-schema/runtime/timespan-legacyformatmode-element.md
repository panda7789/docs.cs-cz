---
title: Element <TimeSpan_LegacyFormatMode>
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
ms.openlocfilehash: 38adde3cd51a96f0e15ed5a0c539e088f2d3b480
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701629"
---
# <a name="timespanlegacyformatmode-element"></a>\<Timespan_legacyformatmode – > – Element
Určuje, zda modul runtime zachová starší chování při formátování operací s <xref:System.TimeSpan?displayProperty=nameWithType> hodnoty.  
  
 \<Konfigurace >  
\<modul runtime >  
<TimeSpan_LegacyFormatMode>  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime používá starší verzi chování při formátování s <xref:System.TimeSpan?displayProperty=nameWithType> hodnoty.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|`false`|Modul runtime neobnoví starší chování při formátování.|  
|`true`|Modul runtime obnoví starší chování při formátování.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], <xref:System.TimeSpan?displayProperty=nameWithType> struktury implementuje <xref:System.IFormattable> rozhraní a podporuje formátování operací pomocí standardních a vlastních formátovacích řetězců. Pokud metoda analýzy se zaznamená řetězce formátu nebo nepodporovaný formát specifikátoru, vyvolá výjimku <xref:System.FormatException>.  
  
 V předchozích verzích rozhraní .NET Framework <xref:System.TimeSpan> struktura neimplementovala <xref:System.IFormattable> a nepodporovalo formátovací řetězce. Nicméně mnoho vývojářů omylem předpokládá se, že <xref:System.TimeSpan> podporoval množinu řetězců formátu a používat je v [složeného formátování operace](../../../../../docs/standard/base-types/composite-formatting.md) s metodami, jako <xref:System.String.Format%2A?displayProperty=nameWithType>. Obvykle Pokud typ implementuje <xref:System.IFormattable> a podporuje formátovací řetězce, volání metody se nepodporovaný formát pro formátování řetězce obvykle vyvolat <xref:System.FormatException>. Ale protože <xref:System.TimeSpan> neimplementovala <xref:System.IFormattable>, modul runtime ignorovat formátovací řetězec a místo toho volat <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metody. To znamená, že i když formátovací řetězce nemělo žádný vliv na operace formátování, jejich přítomnost nezpůsobil ztrátu v <xref:System.FormatException>.  
  
 Pro případy, ve kterých starší kód předá složeného formátování metoda a neplatný řetězec formátu a nemůže být překompilovány tento kód, můžete použít `<TimeSpan_LegacyFormatMode>` prvek, který chcete obnovit starší <xref:System.TimeSpan> chování. Při nastavení `enabled` atribut tohoto elementu `true`, složeného formátování výsledky metody při volání k <xref:System.TimeSpan.ToString?displayProperty=nameWithType> spíše než <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>a <xref:System.FormatException> není vyvolána.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.TimeSpan> objektu a pokusí se ho naformátovat <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> metoda pomocí nepodporované standardní formátovací řetězec.  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 Při spuštění v příkladu [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] nebo s dřívější verzí, se zobrazí následující výstup:  
  
```  
12:30:45  
```  
  
 Tím se liší je výrazně z výstupu pokud příklad spustíte ve [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] nebo novější verzi:  
  
```  
Invalid Format  
```  
  
 Pokud ale přidáte následující konfigurační soubor v příkladu adresáře a poté příklad spustíte ve [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] nebo novější verze, výstup je stejný jako, který v příkladu vytvořen při spuštění [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
