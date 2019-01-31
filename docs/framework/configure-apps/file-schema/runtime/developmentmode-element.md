---
title: Element <developmentMode>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 323bc5d18860c00609a92e33f4a2bd2c832b05a9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290066"
---
# <a name="developmentmode-element"></a>\<developmentmode – > – Element
Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí DEVPATH.  
  
 \<Konfigurace >  
\<modul runtime >  
\<developmentMode>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**developerInstallation**|Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí DEVPATH.|  
  
## <a name="developerinstallation-attribute"></a>developerInstallation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|**true**|Vyhledá sestavení v adresářích určených proměnnou prostředí DEVPATH.|  
|**false**|Není hledat sestavení v adresářích určených proměnnou prostředí DEVPATH. Toto je výchozí|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Toto nastavení použijte jenom v době vývoje. Modul runtime verze sestavení se silným názvem součástí mechanismu DEVPATH nekontroluje. Jednoduše použije první sestavení, které nalezne.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak mají hledat sestavení v adresářích určených proměnnou prostředí DEVPATH pomocí běhového modulu.  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
