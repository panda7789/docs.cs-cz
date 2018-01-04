---
title: "&lt;developmentmode –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a77f93a0dff198821509c2c26f67caa137073ced
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdevelopmentmodegt-element"></a>&lt;developmentmode –&gt; – Element
Určuje, zda běhové prostředí vyhledává sestavení v zadaném proměnnou prostředí DEVPATH adresáře.  
  
 \<Konfigurace >  
\<modul runtime >  
\<developmentmode – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**developerInstallation**|Určuje, zda běhové prostředí vyhledává sestavení v zadaném proměnnou prostředí DEVPATH adresáře.|  
  
## <a name="developerinstallation-attribute"></a>developerInstallation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|**true**|Vyhledá sestavení v zadaném proměnnou prostředí DEVPATH adresáře.|  
|**false**|Nehledá sestavení v zadaném proměnnou prostředí DEVPATH adresáře. Toto je výchozí hodnota|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Toto nastavení používejte pouze v době vývoj. Modul runtime nekontroluje verze na sestavení se silným názvem v mechanismu DEVPATH nalezen. Jednoduše použije první sestavení, které najde.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak způsobí modulu runtime pro vyhledání sestavení v zadaném proměnnou prostředí DEVPATH adresáře.  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
