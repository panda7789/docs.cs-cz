---
title: '&lt;bindingRedirect&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 535519c65aba7ce13703bb33a16b09cde84c3f03
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400605"
---
# <a name="ltbindingredirectgt-element"></a>&lt;bindingRedirect&gt; – Element
Přesměruje jednu verzi sestavení k jiné.  
  
 \<Konfigurace >  
\<modul runtime >  
\<assemblybinding – >  
\<dependentAssembly >  
\<bindingRedirect >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`oldVersion`|Požadovaný atribut.<br /><br /> Určuje verzi sestavení, která byla původně požadována. Číslo verze sestavení má *major.minor.build.revision*. Platné hodnoty pro jednotlivé části tohoto čísla verze jsou 0 až 65535.<br /><br /> Můžete také zadat rozsah verzí v tomto formátu:<br /><br /> *n.n.n.n - n.n.n.n*|  
|`newVersion`|Požadovaný atribut.<br /><br /> Určuje verzi sestavení použít namísto původně požadované verze ve formátu: *n.n.n.n*<br /><br /> Tato hodnota může určit starší verze než `oldVersion`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Žádné||  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`dependentAssembly`|Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení. Používá pro jednotlivá sestavení jeden prvek dependentAssembly.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Při sestavování aplikace rozhraní .NET Framework v rámci sestavení se silným názvem používá aplikace ve výchozím nastavení při spuštění zmíněnou verzi, a to i tehdy, pokud je k dispozici nová verze. Aplikaci však můžete nastavit tak, aby se spustila v rámci novější verze sestavení. Podrobnosti o tom, jak modul runtime používá tyto soubory k určení verze sestavení, které chcete použít, najdete v článku [jak modul Runtime vyhledává sestavení](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Můžete přesměrovat více než jedna verze sestavení zahrnutím více `bindingRedirect` prvky `dependentAssembly` elementu. Můžete také vytvořit přesměrování z novější verze na starší verzi sestavení.  
  
 Explicitní přesměrování vazeb sestavení v konfiguračním souboru aplikace vyžaduje oprávnění zabezpečení. To platí pro přesměrování sestavení rozhraní .NET Framework a sestavení třetích stran. Oprávnění je udělován nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku <xref:System.Security.Permissions.SecurityPermission>. Další informace najdete v tématu [sestavení oprávnění zabezpečení přesměrování vazby](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje způsob přesměrování jedné verze sestavení na jinou.  
  
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
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Přesměrování verzí sestavení](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
