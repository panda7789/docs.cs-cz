---
title: Element <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154420"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly> Element
Určuje sestavení, které poskytuje správce domény aplikace pro výchozí doménu aplikace v procesu.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
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
|`value`|Požadovaný atribut. Určuje zobrazovaný název sestavení, které poskytuje správce domény aplikace pro výchozí doménu aplikace v procesu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li určit typ správce domény aplikace, musíte zadat tento prvek i>element [ \<appDomainManagerType.](appdomainmanagertype-element.md) Pokud některý z těchto prvků není zadán, druhý je ignorován.  
  
 Při načtení výchozí domény <xref:System.TypeLoadException> aplikace je vyvolána, pokud zadané sestavení neexistuje nebo pokud sestavení neobsahuje typ určený [ \<prvkem appDomainManagerType>;](appdomainmanagertype-element.md) a proces se nespustí. Pokud je sestavení nalezeno, ale informace o <xref:System.IO.FileLoadException> verzi se neshodují, je vyvolána.  
  
 Pokud zadáte typ správce domény aplikace pro výchozí doménu aplikace, ostatní domény aplikace vytvořené z výchozí aplikační domény zdědí typ správce domény aplikace. Pomocí <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> vlastností a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> určete jiný typ správce domény aplikace pro novou doménu aplikace.  
  
 Určení typu správce domény aplikace vyžaduje, aby aplikace měla úplný vztah důvěryhodnosti. (Například aplikace spuštěná na ploše má plnou důvěryhodnost.) Pokud aplikace nemá úplný vztah <xref:System.TypeLoadException> důvěryhodnosti, je vyvolána.  
  
 Formát zobrazovaného názvu sestavení naleznete <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> ve vlastnosti.  
  
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
- [\<appDomainManagerType> element](appdomainmanagertype-element.md)
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [SetAppDomainManagerType – metoda](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
