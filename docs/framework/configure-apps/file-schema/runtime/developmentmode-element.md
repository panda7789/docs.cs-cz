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
ms.openlocfilehash: 4573c3a5e0cf64996f2a4e109736d966b754494a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
|**Hodnota TRUE**|Vyhledá sestavení v zadaném proměnnou prostředí DEVPATH adresáře.|  
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
 [Postupy: vyhledání sestavení pomocí mechanismu DEVPATH](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
