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
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154319"
---
# <a name="assemblybinding-element-for-runtime"></a>\<assemblyBinding> – element pro \<runtime>
Obsahuje informace o přesměrování verze sestavení a umístění sestavení.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
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
|**xmlns**|Požadovaný atribut.<br /><br /> Určuje obor názvů XML vyžadovaný pro vazbu sestavení. Jako hodnotu použijte řetězec "urn: schemas-microsoft-com: asm. v1".|  
|**appliesTo**|Určuje verzi modulu runtime, pro kterou je přesměrování sestavení .NET Framework použito. Tento nepovinný atribut používá .NET Framework číslo verze k určení verze, na kterou se vztahuje. Pokud není zadán žádný atribut **AppliesTo** , bude **\<assemblyBinding>** element platit pro všechny verze .NET Framework. Atribut **AppliesTo** byl představen v .NET Framework verze 1,1; ignoruje se .NET Framework verze 1,0. To znamená, že všechny **\<assemblyBinding>** prvky jsou aplikovány při použití .NET Framework verze 1,0, a to i v případě, že je zadán atribut **AppliesTo** .|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|Zapouzdřuje zásady vazeb a umístění sestavení pro sestavení. **\<dependentAssembly>** Pro každé sestavení použijte jednu značku.|  
|[\<probing>](probing-element.md)|Určuje podadresáře, které modul CLR (Common Language Runtime) hledá při načítání sestavení.|  
|[\<publisherPolicy>](publisherpolicy-element.md)|Určuje, zda modul runtime používá zásady vydavatele.|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přesměrovat jednu verzi sestavení na jiný a poskytnout základ kódu.  
  
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
  
 Následující příklad ukazuje, jak použít atribut **AppliesTo** pro přesměrování vazby .NET Framework sestavení.  
  
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

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Přesměrování verzí sestavení](../../redirect-assembly-versions.md)
