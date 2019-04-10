---
title: <assemblyBinding> – element pro <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eec77d4dd42a7b95d1e2cd0e353e2e54746676b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225245"
---
# <a name="assemblybinding-element-for-runtime"></a>\<assemblybinding – > – Element pro \<runtime >
Obsahuje informace o přesměrování verze sestavení a umístění sestavení.  
  
 \<Konfigurace >  
\<modul runtime >  
\<assemblybinding – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**xmlns**|Požadovaný atribut.<br /><br /> Určuje obor názvů XML, vyžaduje se pro vazby sestavení. Použijte řetězec "urn: schémata-microsoft-com:asm.v1" jako hodnotu.|  
|**AppliesTo –**|Určuje verzi modulu runtime, přesměrování sestavení rozhraní .NET Framework se týká. Tento volitelný atribut používá pro určení verze, se vztahuje na číslo verze rozhraní .NET Framework. Pokud ne **appliesTo** atribut zadán,  **\<assemblyBinding >** element platí pro všechny verze rozhraní .NET Framework. **AppliesTo** atribut byla zavedena v rozhraní .NET Framework verze 1.1; je ignorován v rozhraní .NET Framework verze 1.0. To znamená, že všechny  **\<assemblyBinding >** prvky se použijí při použití rozhraní .NET Framework verze 1.0, i když **appliesTo** je zadán atribut.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<dependentAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Zapouzdřuje umístění zásad a sestavení vazby pro sestavení. Použijte jednu  **\<dependentAssembly >** značky pro každé sestavení.|  
|[\<zjišťování >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Určuje modul common language runtime prohledá při načítání sestavení podadresářů.|  
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Určuje, zda modul runtime použije zásady vydavatele.|  
|[\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Určuje úplný název sestavení, které se mají dynamicky načíst při použití částečný název.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob přesměrování jedné verze sestavení do druhého a poskytují základ kódu.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Následující příklad ukazuje způsob použití **appliesTo** atribut pro přesměrování vazby sestavení rozhraní .NET Framework.  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Přesměrování verzí sestavení](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
