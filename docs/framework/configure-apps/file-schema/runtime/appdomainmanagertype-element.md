---
title: Element <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: bae4aa39f9c43480ac2ef984f78834b68646742d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118233"
---
# <a name="appdomainmanagertype-element"></a>\<element > appDomainManagerType
Určuje typ, který slouží jako správce aplikační domény pro výchozí doménu aplikace.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerType >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`value`|Požadovaný atribut. Určuje název typu, včetně oboru názvů, který slouží jako správce aplikační domény pro výchozí doménu aplikace v procesu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li zadat typ Správce aplikační domény, je nutné zadat jak tento prvek, tak [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) elementu. Pokud některý z těchto prvků není zadán, druhá je ignorována.  
  
 Když je načtena výchozí doména aplikace, <xref:System.TypeLoadException> je vyvolána, pokud zadaný typ neexistuje v sestavení určeném [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) elementu; a proces se nepodařilo spustit.  
  
 Když zadáte typ Správce aplikační domény pro výchozí doménu aplikace, ostatní domény aplikace vytvořené z výchozí domény aplikace zdědí typ Správce aplikační domény. Pomocí vlastností <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> určete jiný typ Správce aplikační domény pro novou doménu aplikace.  
  
 Zadání typu správce aplikační domény vyžaduje, aby aplikace měla úplný vztah důvěryhodnosti. (Například aplikace spuštěná na ploše má úplný vztah důvěryhodnosti.) Pokud aplikace nemá úplný vztah důvěryhodnosti, je vyvolána <xref:System.TypeLoadException>.  
  
 Formát typu a oboru názvů je stejný formát, který se používá pro vlastnost <xref:System.Type.FullName%2A?displayProperty=nameWithType>.  
  
 Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že správce aplikační domény pro výchozí doménu aplikace v procesu je typ `MyMgr` v sestavení `AdMgrExample`.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [\<element > appDomainManagerAssembly](appdomainmanagerassembly-element.md)
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [SetAppDomainManagerType – metoda](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
