---
title: '&lt;assemblyIdentity&gt; Element pro &lt;modulu runtime&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0dadf0e07f5e3a9f9152ae7cd57c62721402bff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a>&lt;assemblyIdentity&gt; Element pro &lt;modulu runtime&gt;
Obsahuje identifikační informace o sestavení.  
  
 \<Konfigurace >  
\<modul runtime >  
\<assemblybinding – >  
\<dependentAssembly >  
\<assemblyIdentity >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Požadovaný atribut.<br /><br /> Název sestavení|  
|`culture`|Nepovinný atribut.<br /><br /> Řetězec, který určuje jazyk a zemi nebo oblasti sestavení.|  
|`publicKeyToken`|Nepovinný atribut.<br /><br /> Hexadecimální hodnota, která určuje silného názvu sestavení.|  
|`processorArchitecture`|Nepovinný atribut.<br /><br /> Jeden z hodnoty "x86", "amd64", "msil" nebo "ia64" určení na architektuře procesoru pro sestavení, které obsahuje kód specifické pro procesor. Hodnoty nerozlišují malá a velká písmena. Pokud je atribut přiřadit jinou hodnotu, celý `<assemblyIdentity>` element je ignorována. V tématu <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`amd64`|64bitová verze AMD procesor jenom.|  
|`ia64`|64-bit Intel procesor jenom.|  
|`msil`|Neutrální s ohledem na procesor a bits slova|  
|`x86`|Procesor Intel 32-bit, buď nativní nebo v systému Windows v prostředí systému Windows (WOW) na 64bitové platformě.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`dependentAssembly`|Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení. Použijte jednu `<dependentAssembly>` element pro každé sestavení.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Každý  **\<dependentAssembly >** element musí mít jeden  **\<assemblyIdentity >** podřízený element.  
  
 Pokud `processorArchitecture` atribut nachází, `<assemblyIdentity>` element se vztahuje pouze na sestavení s odpovídající architektuře procesoru. Pokud `processorArchitecture` atribut není k dispozici, `<assemblyIdentity>` element můžete použít k sestavení s žádné architekturu procesoru.  
  
 Následující příklad ukazuje konfigurační soubor pro dvě sestavení se stejným názvem, který cílí na dvě různé architektury procesoru dva a jehož verze údržbě synchronizována. Když se aplikace spouští ve x86 platformy první `<assemblyIdentity>` element platí a druhý je ignorována. Pokud se aplikace provede na platformě než x86 nebo ia64, jak se ignorují.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Pokud konfigurační soubor obsahuje `<assemblyIdentity>` element bez `processorArchitecture` atribut a neobsahuje element, který odpovídá platformě, element bez `processorArchitecture` je použit atribut.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak poskytnout informace o sestavení.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Přesměrování verzí sestavení](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
