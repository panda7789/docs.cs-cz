---
title: Element <CompatSortNLSVersion>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f670bd2030e914cc4431c3325215428570ad46cf
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256605"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion > – Element
Určuje, zda by modul runtime měl při porovnávání řetězců použít starší pořadí řazení.  
  
 \<Konfigurace >  
\<modul runtime >  
\<CompatSortNLSVersion > – Element  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje ID národního prostředí, jehož pořadí řazení se má použít.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|4096|ID národního prostředí, které představuje alternativní pořadí řazení. V tomto případě hodnota 4096 představuje pořadí řazení [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] a starší verze.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Protože porovnání řetězců, řazení a operace velikosti písmen provádět <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> třídy v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] v souladu s standardem Unicode 5.1, výsledky metod porovnání řetězců, jako <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> a <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> může lišit od předchozí verze rozhraní .NET Framework. Pokud vaše aplikace závisí na chování starších verzí, můžete obnovit porovnání řetězců a pravidla řazení používaná v [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] a předchozích verzích přidáním `<CompatSortNLSVersion>` prvku v konfiguračním souboru vaší aplikace.  
  
> [!IMPORTANT]
>  Obnovení starších pravidel porovnání a řazení řetězců vyžaduje, aby v místním systému byla k dispozici dynamická knihovna sort00001000.dll.  
  
 Také vám pomůže starší pravidla řazení a porovnání ve specifické aplikační doméně předáním řetězce "NetFx40_Legacy20SortingBehavior" <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metoda při vytváření domény aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě <xref:System.String> a volá <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodu pro jejich porovnání pomocí konvencí aktuální jazykové verze.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Při spuštění v příkladu [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], zobrazí se následující výstup.  
  
```  
sta follows a in the sort order.  
```  
  
 Toto je zcela liší od výstupu, který se zobrazí, pokud příklad spustíte ve [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```  
sta equals a in the sort order.  
```  
  
 Pokud ale přidáte následující konfigurační soubor v příkladu adresáře a poté příklad spustíte ve [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], výstup je stejný jako, který v příkladu vytvořen při spuštění [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
