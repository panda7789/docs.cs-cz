---
title: '&lt;Vlastnost assemblyIdentity&gt; – Element pro &lt;modulu runtime&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2b0d7968ce2cf8f326004c9e564cb2e7912c1a0a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077340"
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a>&lt;Vlastnost assemblyIdentity&gt; – Element pro &lt;modulu runtime&gt;
Obsahuje identifikační informace o sestavení.  
  
 \<Konfigurace >  
\<modul runtime >  
\<assemblybinding – >  
\<dependentAssembly >  
\<Vlastnost assemblyIdentity >  
  
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
|`culture`|Nepovinný atribut.<br /><br /> Řetězec, který určuje jazyk a zemi/oblast sestavení.|  
|`publicKeyToken`|Nepovinný atribut.<br /><br /> Šestnáctková hodnota, která udává silný název sestavení.|  
|`processorArchitecture`|Nepovinný atribut.<br /><br /> Jedna z hodnot "x86", "amd64", "msil" nebo "ia64" zadání sestavení, která obsahuje kód závislý na procesoru na architektuře procesoru. Hodnoty nerozlišují malá a velká písmena. Pokud je atribut přiřadit jinou hodnotu, celý `<assemblyIdentity>` prvek je ignorován. Zobrazit <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>Vlastnost processorArchitecture atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`amd64`|64-bit AMD procesor pouze.|  
|`ia64`|64-bit Intel procesor pouze.|  
|`msil`|Neutrální s ohledem na procesor a bits slova|  
|`x86`|Procesor Intel 32-bit, buď native nebo ve Windows v prostředí Windows (WOW) na 64bitové platformě.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`dependentAssembly`|Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení. Použijte jednu `<dependentAssembly>` – element pro každé sestavení.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Každý  **\<dependentAssembly >** element musí mít jeden  **\<assemblyIdentity >** podřízený element.  
  
 Pokud `processorArchitecture` atribut je k dispozici, `<assemblyIdentity>` element platí pouze pro sestavení s odpovídající architektuře procesoru. Pokud `processorArchitecture` atribut není k dispozici, `<assemblyIdentity>` element můžete použít pro sestavení jakékoli architektuře procesoru.  
  
 Následující příklad ukazuje konfigurační soubor pro dvě sestavení se stejným názvem, jejichž cílem dvě různé dvě architektury procesoru, a jejichž verze ještě nebyla zachována synchronizována. Když se aplikace spustí na x86 platformy první `<assemblyIdentity>` vztahuje k elementu a druhý je ignorován. Pokud aplikace provádí na platformě jiné než x86 nebo ia64, obě jsou ignorovány.  
  
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
  
 Pokud konfigurační soubor obsahuje `<assemblyIdentity>` element bez `processorArchitecture` atribut a neobsahuje element, který odpovídá platformě elementu bez `processorArchitecture` atribut se používá.  
  
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
