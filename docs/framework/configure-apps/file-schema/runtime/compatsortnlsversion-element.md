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
ms.openlocfilehash: 575d44ad9ecf445ba5d4b7fbe47032127ccb33ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252737"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion – element >
Určuje, zda by modul runtime měl při porovnávání řetězců použít starší pořadí řazení.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<CompatSortNLSVersion>**  
  
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
  
|Value|Popis|  
|-----------|-----------------|  
|4096|ID národního prostředí, které představuje alternativní pořadí řazení. V tomto případě 4096 představuje pořadí řazení .NET Framework 3,5 a starších verzí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že porovnání řetězců, řazení a operace s <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> velkými a malými písmeny prováděné třídou v .NET Framework 4 odpovídají standardu Unicode 5,1, výsledky <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> metod <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> porovnání řetězců, jako jsou a se mohou lišit od předchozí verze .NET Framework. Pokud vaše aplikace závisí na starším chování, můžete obnovit pravidla porovnání a řazení řetězců používané v .NET Framework 3,5 a starších verzích zahrnutím `<CompatSortNLSVersion>` elementu do konfiguračního souboru aplikace.  
  
> [!IMPORTANT]
> Obnovení starších pravidel porovnání a řazení řetězců vyžaduje, aby v místním systému byla k dispozici dynamická knihovna sort00001000.dll.  
  
 Můžete také použít starší řazení řetězců a pravidla porovnávání v konkrétní aplikační doméně předáním řetězce "NetFx40_Legacy20SortingBehavior" do <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metody při vytváření domény aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří instanci dvou <xref:System.String> objektů a <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> zavolá metodu pro jejich porovnání pomocí konvencí aktuální jazykové verze.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Když spustíte příklad na .NET Framework 4, zobrazí se následující výstup.  
  
```  
sta follows a in the sort order.  
```  
  
 To se zcela liší od výstupu, který se zobrazí při spuštění příkladu na .NET Framework 3,5.  
  
```  
sta equals a in the sort order.  
```  
  
 Pokud však do adresáře s příkladem přidáte následující konfigurační soubor a poté spustíte příklad na .NET Framework 4, výstup je stejný jako v příkladu, který byl vytvořen v příkladu při spuštění v .NET Framework 3,5.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
