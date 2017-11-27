---
title: "&lt;Compatsortnlsversion –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d82187248e743d9081a97411f2ff2ad84707e61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompatsortnlsversiongt-element"></a>&lt;Compatsortnlsversion –&gt; – Element
Určuje, zda by modul runtime měl při porovnávání řetězců použít starší pořadí řazení.  
  
 \<Konfigurace >  
\<modul runtime >  
\<Compatsortnlsversion – > elementu  
  
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
|4096|ID národního prostředí, které představuje alternativní pořadí řazení. V takovém případě 4096 představuje pořadí řazení [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] a starší verze.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Protože porovnání řetězců, řazení a operace velká a malá písmena provádí <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> třídy v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] odpovídat standardem Unicode 5.1, výsledky metody pro porovnání řetězců, jako <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> a <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> se můžou lišit od předchozí verze rozhraní .NET Framework. Pokud je aplikace závislá na starší verze chování, můžete obnovit porovnání řetězců a řazení pravidla použít v [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] a starší verze, včetně `<CompatSortNLSVersion>` element v konfiguračním souboru aplikace.  
  
> [!IMPORTANT]
>  Obnovení starších pravidel porovnání a řazení řetězců vyžaduje, aby v místním systému byla k dispozici dynamická knihovna sort00001000.dll.  
  
 Také můžete pravidla řazení a porovnání starší verze řetězec ve specifické aplikační doméně předáním řetězec "NetFx40_Legacy20SortingBehavior" <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metoda při vytváření domény aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě instance <xref:System.String> objekty a volání <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metoda k porovnání je pomocí konvencí aktuální jazykové verze.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Při spuštění v příkladu [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], zobrazí se následující výstup.  
  
```  
sta follows a in the sort order.  
```  
  
 Toto je zcela liší od výstupu, který se zobrazí při spuštění v příkladu na [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```  
sta equals a in the sort order.  
```  
  
 Ale pokud přidáte následujícího konfiguračního souboru v příkladu je adresáře a spusťte v příkladu [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], je stejná jako vyprodukované v příkladu, když se spustí na výstup [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
