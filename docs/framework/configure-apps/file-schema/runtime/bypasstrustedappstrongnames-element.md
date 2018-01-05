---
title: "&lt;bypasstrustedappstrongnames –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0343aef083076249325b9577f90964d066867f24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a>&lt;bypasstrustedappstrongnames –&gt; – Element
Určuje, jestli se má vynechat ověřování silné názvy na plné důvěryhodnosti sestavení, která jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>.  
  
 \<Konfigurace >  
\<modul runtime >  
\<bypasstrustedappstrongnames – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda je povolena funkce jednorázové přihlášení, která zabraňuje ověřování silných názvů pro sestavení plné důvěryhodnosti. Pokud je tato funkce povolena, nejsou silné názvy ověřit správnost, když je načteno sestavení. Výchozí hodnota je `true`.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`true`|Nejsou k ověřování podpisů silného názvu sestavení plné důvěryhodnosti při sestavení jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>. Toto nastavení je výchozí.|  
|`false`|Jsou k ověřování podpisů silného názvu sestavení plné důvěryhodnosti při sestavení jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>. Podpis silného názvu, se kontroluje jenom na podpis správnost; není porovná jiné silný název pro shodu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce obejití silného názvu zabraňuje režii ověřit podpis silného názvu sestavení plné důvěryhodnosti.  
  
 Funkce obcházení vztahuje na všechny sestavení, který je podepsaný se silným názvem, který má následující vlastnosti:  
  
-   Bez plně důvěryhodná <xref:System.Security.Policy.StrongName> důkaz (například má `MyComputer` zónu důkaz).  
  
-   Načíst do plně důvěryhodné <xref:System.AppDomain>.  
  
-   Načtené z umístění v rámci <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost této <xref:System.AppDomain>.  
  
-   Podepsáno bez zpoždění.  
  
> [!NOTE]
>  Pokud funkce jednorázové přihlášení je vypnutá pro všechny aplikace v počítači pomocí klíče registru, toto nastavení konfigurační soubor nemá žádný vliv. Další informace najdete v tématu [postupy: Zákaz funkce obejití silného názvu](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit způsob chování, která ověřuje podpis silného názvu sestavení plné důvěryhodnosti.  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Postupy: Zákaz funkce obejití silného názvu](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
