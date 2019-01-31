---
title: Element <probing>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f66ba8307a33a0a0b80cd71dd027852f67c03f72
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257042"
---
# <a name="probing-element"></a>\<zjišťování > – Element
Určuje základní podadresářích aplikace pro modul common language runtime pro hledání při načítání sestavení.  
  
 \<Konfigurace >  
\<modul runtime >  
\<assemblybinding – >  
\<zjišťování >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`privatePath`|Požadovaný atribut.<br /><br /> Určuje podadresáře základního adresáře aplikace, které mohou obsahovat sestavení. Vymezení každý podadresář oddělte středníkem.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit základní podadresářích aplikace, které by měl modul runtime vyhledat sestavení.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Určení umístění sestavení](../../../../../docs/framework/configure-apps/specify-assembly-location.md)
- [Jak běhové prostředí vyhledává sestavení](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
