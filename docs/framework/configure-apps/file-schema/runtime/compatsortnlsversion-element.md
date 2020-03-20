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
ms.openlocfilehash: 30afeb2ab9380db75cbeb723ea15a23e4313c9e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154267"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion> Element
Určuje, zda by modul runtime měl při porovnávání řetězců použít starší pořadí řazení.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**  
  
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
|4 096|ID národního prostředí, které představuje alternativní pořadí řazení. V tomto případě 4096 představuje pořadí řazení rozhraní .NET Framework 3.5 a starší verze.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že operace porovnání <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> řetězců, řazení a pouzdře prováděné třídou v rozhraní .NET <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> Framework <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> 4 odpovídají standardu Unicode 5.1, výsledky metod porovnání řetězců, jako jsou a mohou se lišit od předchozích verzí rozhraní .NET Framework. Pokud vaše aplikace závisí na starší chování, můžete obnovit porovnání řetězců a řazení pravidla používaná v `<CompatSortNLSVersion>` rozhraní .NET Framework 3.5 a starší verze zahrnutím prvku v konfiguračním souboru aplikace.  
  
> [!IMPORTANT]
> Obnovení starších pravidel porovnání a řazení řetězců vyžaduje, aby v místním systému byla k dispozici dynamická knihovna sort00001000.dll.  
  
 Starší pravidla řazení a porovnání řetězců můžete také použít v konkrétní doméně <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> aplikace předáním řetězce "NetFx40_Legacy20SortingBehavior" metodě při vytváření domény aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad inkoniátuje <xref:System.String> <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> dva objekty a volá metodu k jejich porovnání pomocí konvencí aktuální jazykové verze.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Při spuštění příkladu v rozhraní .NET Framework 4 se zobrazí následující výstup:
  
```console
sta follows a in the sort order.  
```  
  
 To je zcela odlišné od výstupu, který se zobrazí při spuštění příkladu v rozhraní .NET Framework 3.5:
  
```console
sta equals a in the sort order.  
```  
  
 Pokud však přidáte následující konfigurační soubor do adresáře příkladu a potom spustíte příklad v rozhraní .NET Framework 4, výstup je shodný s výstupem vytvořeným v příkladu při spuštění v rozhraní .NET Framework 3.5.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
