---
title: Element <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 083e3ba21dcd196eacfe3d9fd649c211da9dc125
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252853"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly – element >
Určuje sestavení, které poskytuje správce aplikační domény pro výchozí doménu aplikace v procesu.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`value`|Požadovaný atribut. Určuje zobrazovaný název sestavení, které poskytuje správce aplikační domény pro výchozí doménu aplikace v procesu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li zadat typ Správce aplikační domény, je nutné zadat jak tento prvek, tak [ \<i prvek appDomainManagerType >](appdomainmanagertype-element.md) . Pokud některý z těchto prvků není zadán, druhá je ignorována.  
  
 Když je načtena výchozí doména aplikace, <xref:System.TypeLoadException> je vyvolána, pokud zadané sestavení neexistuje nebo pokud sestavení neobsahuje typ určený [ \<prvkem appDomainManagerType >](appdomainmanagertype-element.md) ; a proces se nezdařil. Čína. Pokud je sestavení nalezeno, ale informace o verzi se neshodují, <xref:System.IO.FileLoadException> je vyvolána.  
  
 Když zadáte typ Správce aplikační domény pro výchozí doménu aplikace, ostatní domény aplikace vytvořené z výchozí domény aplikace zdědí typ Správce aplikační domény. Pomocí vlastností <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> a určete jiný typ Správce aplikační domény pro novou doménu aplikace. <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
  
 Zadání typu správce aplikační domény vyžaduje, aby aplikace měla úplný vztah důvěryhodnosti. (Například aplikace spuštěná na ploše má úplný vztah důvěryhodnosti.) Pokud aplikace nemá úplný vztah důvěryhodnosti, <xref:System.TypeLoadException> je vyvolána výjimka.  
  
 Pro formát zobrazovaného názvu sestavení se podívejte na <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastnost.  
  
 Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že správce aplikační domény pro výchozí doménu aplikace v procesu je `MyMgr` typ `AdMgrExample` v sestavení.  
  
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
- [\<appDomainManagerType> Element](appdomainmanagertype-element.md)
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [SetAppDomainManagerType – metoda](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
