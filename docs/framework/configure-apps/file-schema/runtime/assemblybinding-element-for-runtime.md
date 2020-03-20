---
title: Element <assemblyBinding> pro <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154319"
---
# <a name="assemblybinding-element-for-runtime"></a>\<assemblyBinding> \<Element pro> za běhu
Obsahuje informace o přesměrování verze sestavení a umístění sestavení.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
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
|**Xmlns**|Požadovaný atribut.<br /><br /> Určuje obor názvů XML požadovaný pro vazbu sestavení. Jako hodnotu použijte řetězec "urn:schemas-microsoft-com:asm.v1".|  
|**platíTo**|Určuje verzi runtime, na kterou se vztahuje přesměrování sestavení rozhraní .NET Framework. Tento volitelný atribut používá číslo verze rozhraní .NET Framework k označení, na jakou verzi se vztahuje. Pokud není zadán žádný atribut **appliesTo,** element ** \<assemblyBinding>** se vztahuje na všechny verze rozhraní .NET Framework. Atribut **appliesTo** byl zaveden v rozhraní .NET Framework verze 1.1; rozhraní .NET Framework verze 1.0 jej ignoruje. To znamená, že všechny ** \<elementy assemblyBinding>** jsou použity při použití rozhraní .NET Framework verze 1.0, i když je zadán atribut **appliesTo.**|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|Zapouzdřuje zásady vazby a umístění sestavení pro sestavení. Pro ** \<** každou sestavu použijte jednu značku dependentassembly>.|  
|[\<sondování>](probing-element.md)|Určuje podadresáře, které při načítání sestavení vyhledává běžný jazyk.|  
|[\<vydavatelZásady>](publisherpolicy-element.md)|Určuje, zda program runtime použije zásadu vydavatele.|  
|[\<kvalifikačnímontážní>](qualifyassembly-element.md)|Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přesměrovat jednu verzi sestavení na jinou a poskytnout základ kódu.  
  
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
  
 Následující příklad ukazuje, jak použít **atribut appliesTo** k přesměrování vazby sestavení rozhraní .NET Framework.  
  
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

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Přesměrování verzí sestavení](../../redirect-assembly-versions.md)
