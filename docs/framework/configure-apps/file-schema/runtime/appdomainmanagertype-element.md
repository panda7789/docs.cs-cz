---
title: Element <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154421"
---
# <a name="appdomainmanagertype-element"></a>\<appDomainManagerType> element
Určuje typ, který slouží jako správce domény aplikace pro výchozí doménu aplikace.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>appDomainManagerType**  
  
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
|`value`|Požadovaný atribut. Určuje název typu, včetně oboru názvů, který slouží jako správce domény aplikace pro výchozí doménu aplikace v procesu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li určit typ správce domény aplikace, musíte zadat tento prvek i [ \<element>appDomainManagerAssembly.](appdomainmanagerassembly-element.md) Pokud některý z těchto prvků není zadán, druhý je ignorován.  
  
 Při načtení výchozí domény <xref:System.TypeLoadException> aplikace je vyvolána, pokud zadaný typ neexistuje v sestavení, které je určeno [ \<prvkem appDomainManagerAssembly>;](appdomainmanagerassembly-element.md) a proces se nespustí.  
  
 Pokud zadáte typ správce domény aplikace pro výchozí doménu aplikace, ostatní domény aplikace vytvořené z výchozí aplikační domény zdědí typ správce domény aplikace. Pomocí <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> vlastností a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> určete jiný typ správce domény aplikace pro novou doménu aplikace.  
  
 Určení typu správce domény aplikace vyžaduje, aby aplikace měla úplný vztah důvěryhodnosti. (Například aplikace spuštěná na ploše má plnou důvěryhodnost.) Pokud aplikace nemá úplný vztah <xref:System.TypeLoadException> důvěryhodnosti, je vyvolána.  
  
 Formát typu a oboru názvů je stejný formát, <xref:System.Type.FullName%2A?displayProperty=nameWithType> který se používá pro vlastnost.  
  
 Tento konfigurační prvek je k dispozici pouze v rozhraní .NET Framework 4 a novější.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že správce domény aplikace pro `MyMgr` výchozí aplikační `AdMgrExample` doménu procesu je typ v sestavení.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [\<appDomainManagerAssembly> Element](appdomainmanagerassembly-element.md)
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [SetAppDomainManagerType – metoda](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
