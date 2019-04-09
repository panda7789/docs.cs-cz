---
title: <appDomainManagerType> Prvek
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7aa13d26ac11ed624caa4c9704325f2d604418bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164213"
---
# <a name="appdomainmanagertype-element"></a>\<appDomainManagerType> Element
Určuje typ, který slouží jako správce domény aplikace pro výchozí domény aplikace.  
  
 \<Konfigurace >  
\<modul runtime >  
\<appDomainManagerType>  
  
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
|`value`|Požadovaný atribut. Určuje název typu včetně oboru názvů, který slouží jako správce domény aplikace pro výchozí domény aplikace v procesu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li určit typ správce domény aplikace, je nutné zadat obě tento element a [ \<appdomainmanagerassembly – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) elementu. Pokud některý z těchto prvků není zadán, druhý se ignoruje.  
  
 Při načítání výchozí domény aplikace <xref:System.TypeLoadException> je vyvolána, pokud zadaný typ neexistuje v sestavení, která je zadána [ \<appdomainmanagerassembly – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element; a proces nebude moci bylo zahájeno.  
  
 Když zadáte typ správce domény aplikace výchozí aplikační domény, dědí jiných domén aplikace vytvořené z výchozí domény aplikace typ správce domény aplikace. Použití <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> vlastnosti zadat typ správce různých aplikační domény pro novou doménu aplikace.  
  
 Určení typu správce domény aplikace vyžaduje, aby aplikace mít plnou důvěryhodnost. (Například aplikace běžící v desktopovém má úplný vztah důvěryhodnosti.) Pokud aplikace nemá plnou důvěryhodnost <xref:System.TypeLoadException> je vyvolána výjimka.  
  
 Formát typu a obor názvů je stejný formát, který se používá pro <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnost.  
  
 Tento prvek konfigurace je k dispozici pouze v [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] a novější.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že je aplikace správce domény pro doménu aplikace výchozí procesu `MyMgr` zadejte `AdMgrExample` sestavení.  
  
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
- [\<appDomainManagerAssembly> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [SetAppDomainManagerType – metoda](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
