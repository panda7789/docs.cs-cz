---
title: "&lt;codeBase&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 272a4262295b5dd67414dd0ef6523f90b2125836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcodebasegt-element"></a>&lt;codeBase&gt; – Element
Určuje, kde sestavení modul common language runtime.  
  
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
|`href`|Požadovaný atribut.<br /><br /> Určuje adresu URL, kde zadaná verze sestavení modulu runtime.|  
|`version`|Požadovaný atribut.<br /><br /> Určuje verzi sestavení, ve kterém základu kódu se vztahuje na. Formát čísla verze sestavení je *major.minor.build.revision*.|  
  
## <a name="version-attribute"></a>verze atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Platné hodnoty pro každou část číslo verze jsou 0 až 65535.|Nelze použít.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`buildproviders`|Definuje kolekci zprostředkovatelů sestavení používá ke kompilaci vlastních souborů prostředků. Může mít libovolný počet poskytovatele sestavení.|  
|`compilation`|Nakonfiguruje všechna nastavení kompilace, která používá technologii ASP.NET.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`System.web`|Určuje kořenový element pro konfigurační oddíl technologie ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
 Pro modul runtime používat  **\<codeBase >** nastavení v konfiguračním souboru počítače nebo soubor zásad vydavatele, soubor musí také přesměrování verze sestavení. Konfigurační soubory aplikace mohou mít nastavení codebase bez přesměrování verze sestavení. Po určení, které verze sestavení se má použít, se vztahuje codebase nastavení ze souboru, který určuje verzi modulu runtime. Pokud je uvedené žádné codebase, sondy modulu runtime pro sestavení obvyklým způsobem.  
  
 Pokud sestavení se silným názvem, codebase nastavení může být kdekoli na místního intranetu nebo Internetu. Pokud je sestavení privátní sestavení, nastavení codebase musí být cesta relativní vzhledem k adresáři aplikace.  
  
 Pro sestavení bez silný název, verze ignorováno a zavaděč používá první vzhled \<codebase > uvnitř \<dependentAssembly >. Pokud je položka v konfiguračním souboru aplikace, který provede přesměrování vazby sestavení, přesměrování bude mít přednost i v případě, že verze sestavení neshoduje vazby požadavku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k určení, kde sestavení modulu runtime.  
  
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
