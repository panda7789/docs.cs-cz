---
title: Element <publisherPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be87c91b798256f3913779bdbe36f3548066018b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55253935"
---
# <a name="publisherpolicy-element"></a>\<publisherPolicy > – Element
Určuje, zda modul runtime použije zásady vydavatele.  
  
 \<Konfigurace >  
\<modul runtime >  
\<assemblybinding – >  
\<dependentAssembly >  
\<publisherPolicy>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`apply`|Určuje, jestli se má použít zásady vydavatele.|  
  
## <a name="apply-attribute"></a>použít atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`yes`|Použije zásady vydavatele. Toto je výchozí nastavení.|  
|`no`|Doporučení se netýká zásad vydavatele.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Při vydání nové verze sestavení dodavatele součástí můžete dodavatele obsahují zásad vydavatele, takže aplikace, které používají starší verzi nyní používat novou verzi. Chcete-li určit, jestli se má použít pro konkrétní sestavení zásad vydavatele, umístěte  **\<publisherPolicy >** prvek  **\<dependentAssembly >** element.  
  
 Ve výchozím nastavení **použít** atribut je **Ano**. Nastavení **použít** atribut **žádné** přepíše jakékoli předchozí **Ano** nastavení sestavení.  
  
 Oprávnění je požadováno pro aplikace explicitně ignorovat pomocí zásady vydavatele [ \<publisherPolicy použít = "žádný" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) prvku v konfiguračním souboru aplikace. Oprávnění je udělován nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku <xref:System.Security.Permissions.SecurityPermission>. Další informace najdete v tématu [sestavení oprávnění zabezpečení přesměrování vazby](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vypne zásady vydavatele pro sestavení, `myAssembly`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Jak běhové prostředí vyhledává sestavení](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Přesměrování verzí sestavení](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
