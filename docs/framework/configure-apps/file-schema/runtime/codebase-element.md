---
title: '&lt;základ kódu&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d7563d3a0ba545bfd8d1b80981fcce607d230873
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028212"
---
# <a name="ltcodebasegt-element"></a>&lt;základ kódu&gt; – Element
Určuje, kde najít sestavení modulu common language runtime.  
  
 \<Konfigurace >  
\<modul runtime >  
\<assemblybinding – >  
\<dependentAssembly >  
\<codeBase >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`href`|Požadovaný atribut.<br /><br /> Určuje adresu URL, kde modul runtime může najít zadanou verzi sestavení.|  
|`version`|Požadovaný atribut.<br /><br /> Určuje verzi sestavení, ve kterém základu kódu se vztahuje na. Číslo verze sestavení má *major.minor.build.revision*.|  
  
## <a name="version-attribute"></a>verze atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Platné hodnoty pro každou část čísla verze jsou 0 až 65535.|Nelze použít.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`buildproviders`|Definuje kolekci zprostředkovatelů sestavení používá ke kompilaci soubory vlastních prostředků. Můžete mít libovolný počet poskytovatelé sestavení.|  
|`compilation`|Nakonfiguruje všechna nastavení kompilace, která používá ASP.NET.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`System.web`|Určuje kořenový element části o konfiguraci technologie ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
 Pro modul runtime pro použití  **\<codeBase >** nastavení v konfiguračním souboru počítače nebo soubor zásad vydavatele, soubor musíte také vytvořit přesměrování verze sestavení. Konfigurační soubory aplikace mohou mít nastavení základu kódu bez přesměrování verze sestavení. Po určení verze sestavení, které chcete použít, se vztahuje nastavení základu kódu ze souboru, který určuje verzi modulu runtime. Pokud je uveden žádný základ kódu, modul runtime sondy pro sestavení obvyklým způsobem.  
  
 Pokud sestavení se silným názvem, nastavení základu kódu může být kdekoli na místním intranetu nebo Internetu. Je-li soukromé sestavení je sestavení, nastavení základu kódu musí být cesta relativní k adresáři vaší aplikace.  
  
 Pro sestavení bez silného názvu, verze ignorovány a používá zavaděč první výskyt \<codebase > uvnitř \<dependentAssembly >. Pokud existuje položka v konfiguračním souboru aplikace, který přesměrovává vazby na jiné sestavení, přesměrování bude mít přednost i v případě, že verze sestavení neshoduje požadavek na vytvoření vazby.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, kde najít sestavení modulu runtime.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Určení umístění sestavení](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
