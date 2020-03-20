---
title: Element <assemblyIdentity> pro <runtime>
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154306"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<assemblyIdentity> \<Element pro> za běhu
Obsahuje identifikační informace o sestavení.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
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
|`culture`|Nepovinný atribut.<br /><br /> Řetězec, který určuje jazyk a zemi nebo oblast sestavení.|  
|`publicKeyToken`|Nepovinný atribut.<br /><br /> Šestnáctková hodnota, která určuje silný název sestavení.|  
|`processorArchitecture`|Nepovinný atribut.<br /><br /> Jedna z hodnot "x86", "amd64", "msil" nebo "ia64", určující architekturu procesoru pro sestavení, které obsahuje kód specifický pro procesor. Hodnoty nejsou rozlišována malá a velká písmena. Pokud je atribut přiřazen jinou `<assemblyIdentity>` hodnotu, celý prvek je ignorován. Viz třída <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>atribut architektury procesoru  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`amd64`|Pouze architektura AMD x86-64.|  
|`ia64`|Pouze architektura Intel Itanium.|  
|`msil`|Neutrální s ohledem na procesor a bity na slovo.|  
|`x86`|32bitový procesor x86, nativní nebo v prostředí Windows v systému Windows (WOW) na 64bitové platformě.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`dependentAssembly`|Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení. Pro `<dependentAssembly>` každé sestavení použijte jeden prvek.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Každý ** \<prvek dependentAssembly>** musí mít jeden ** \<prvek identity identity>** podřízeného prvku.  
  
 Pokud `processorArchitecture` je atribut přítomen, `<assemblyIdentity>` prvek se vztahuje pouze na sestavení s odpovídající architekturou procesoru. Pokud `processorArchitecture` atribut není k `<assemblyIdentity>` dispozici, prvek lze použít pro sestavení s libovolnou architekturou procesoru.  
  
 Následující příklad ukazuje konfigurační soubor pro dvě sestavení se stejným názvem, které se zaměřují na dvě různé architektury procesoru a jejichž verze nebyly udržovány v synchronizaci. Když se aplikace spustí na platformě `<assemblyIdentity>` x86, použije se první prvek a druhý je ignorován. Pokud se aplikace spustí na jiné platformě než x86 nebo ia64, jsou ignorovány.  
  
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
  
 Pokud konfigurační `<assemblyIdentity>` soubor `processorArchitecture` obsahuje prvek bez atributu a neobsahuje prvek, `processorArchitecture` který odpovídá platformě, prvek bez atributu se používá.  
  
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

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Přesměrování verzí sestavení](../../redirect-assembly-versions.md)
