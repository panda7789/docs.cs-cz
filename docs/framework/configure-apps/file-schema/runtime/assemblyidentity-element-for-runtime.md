---
title: <assemblyIdentity> – element pro <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154306"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<assemblyIdentity> – element pro \<runtime>
Obsahuje identifikační informace o sestavení.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
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
|`publicKeyToken`|Nepovinný atribut.<br /><br /> Hexadecimální hodnota, která určuje silný název sestavení.|  
|`processorArchitecture`|Nepovinný atribut.<br /><br /> Jedna z hodnot "x86", "amd64", "MSIL" nebo "ia64" s určením architektury procesoru pro sestavení, které obsahuje kód specifický pro procesor. V hodnotách se nerozlišují velká a malá písmena. Pokud má atribut přiřazenou jinou hodnotu, `<assemblyIdentity>` je ignorován celý prvek. Viz třída <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|`amd64`|Pouze architektura AMD X86-64.|  
|`ia64`|Jenom architektura Intel Itanium.|  
|`msil`|Neutrální s ohledem na procesor a bity na slovo.|  
|`x86`|32 procesor x86, buď nativní, nebo v prostředí Windows on Windows (WOW) na platformě 64.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`dependentAssembly`|Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení. `<dependentAssembly>`Pro každé sestavení použijte jeden prvek.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Každý **\<dependentAssembly>** element musí mít jeden **\<assemblyIdentity>** podřízený element.  
  
 Pokud `processorArchitecture` je přítomen atribut, `<assemblyIdentity>` element se vztahuje pouze na sestavení s odpovídající architekturou procesoru. Pokud `processorArchitecture` atribut není přítomen, `<assemblyIdentity>` element může platit pro sestavení s libovolnou architekturou procesoru.  
  
 Následující příklad ukazuje konfigurační soubor pro dvě sestavení se stejným názvem, která cílí na dvě různé architektury procesorů a jejichž verze nebyly v synchronizaci synchronizovány. Když se aplikace spustí na platformě x86, použije se první `<assemblyIdentity>` prvek a druhý se ignoruje. Pokud je aplikace spuštěna na jiné platformě než x86 nebo ia64, obě jsou ignorovány.  
  
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
  
 Pokud konfigurační soubor obsahuje prvek bez `<assemblyIdentity>` `processorArchitecture` atributu a neobsahuje prvek, který odpovídá platformě, `processorArchitecture` je použit prvek bez atributu.  
  
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

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Přesměrování verzí sestavení](../../redirect-assembly-versions.md)
