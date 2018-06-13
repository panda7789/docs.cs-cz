---
title: '&lt;assemblybinding –&gt; Element pro &lt;modulu runtime&gt;'
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
ms.openlocfilehash: d84c134b8e2b048f39836bbc10af06039e96719e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746173"
---
# <a name="ltassemblybindinggt-element-for-ltruntimegt"></a>&lt;assemblybinding –&gt; Element pro &lt;modulu runtime&gt;
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
|**atribut xmlns**|Požadovaný atribut.<br /><br /> Určuje obor názvů XML, které jsou potřebné pro sestavení – vazby. Použít řetězec "urn: schémata-microsoft-com:asm.v1" jako hodnotu.|  
|**AppliesTo –**|Určuje přesměrování sestavení rozhraní .NET Framework se vztahuje na verzi modulu runtime. Tento volitelný atribut používá označíte, jaká verze se vztahuje na číslo verze rozhraní .NET Framework. Pokud žádné **AppliesTo –** atribut zadán,  **\<assemblybinding – >** element platí pro všechny verze rozhraní .NET Framework. **AppliesTo –** atribut byla zavedena v rozhraní .NET Framework verze 1.1; je ignorován v rozhraní .NET Framework verze 1.0. To znamená, že všechny  **\<assemblybinding – >** prvky se použijí při použití rozhraní .NET Framework verze 1.0, i když **AppliesTo –** zadán atribut.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<dependentAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Zapouzdří vazby zásady a sestavení umístění pro sestavení. Použijte jednu  **\<dependentAssembly >** značky pro každé sestavení.|  
|[\<Zkušební fáze >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Určuje podadresáře modul common language runtime vyhledá při načítání sestavení.|  
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Určuje, zda modul runtime aplikuje zásady vydavatele.|  
|[\<qualifyassembly – >](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Určuje úplný název sestavení, které by měl být dynamicky načíst, pokud je použít částečný název.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k přesměrování jednu verzi sestavení do druhého a poskytují základu kódu.  
  
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
  
 Následující příklad ukazuje, jak používat **AppliesTo –** atribut přesměrování vazby sestavení rozhraní .NET Framework.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Přesměrování verzí sestavení](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
