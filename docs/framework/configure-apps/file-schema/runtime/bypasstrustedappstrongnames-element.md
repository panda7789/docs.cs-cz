---
title: <bypassTrustedAppStrongNames> Prvek
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c39d9a1e3da9cccb2f027e9597a6f2272d187ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179137"
---
# <a name="bypasstrustedappstrongnames-element"></a>\<bypassTrustedAppStrongNames> Element
Určuje, zda obejít ověřování silných názvů na plně důvěryhodných sestavení, která jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>.  
  
 \<Konfigurace >  
\<modul runtime >  
\<bypassTrustedAppStrongNames>  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda je povolena funkce jednorázové přihlášení, které se vyhýbají ověřování silných názvů pro plně důvěryhodná sestavení. Pokud je tato funkce povolena, silné názvy nejsou ověřit správnost při sestavení je načteno. Výchozí hodnota je `true`.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|`true`|Podpisy silného názvu na sestavení s úplnou důvěryhodností nejsou ověřovány při sestavení jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>. Toto nastavení je výchozí.|  
|`false`|Podpisy silného názvu na sestavení s úplnou důvěryhodností ověřovány při sestavení jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>. Podpis silného názvu se kontroluje jenom u podpisu správnosti; není porovnání s jinou silným názvem pro shodu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce obejití silného názvu se vyhnete režii ověření podpisu se silným názvem sestavení úplného vztahu důvěryhodnosti.  
  
 Funkce obejití vztahuje na všechny sestavení je podepsáno silným názvem a, který má následující vlastnosti:  
  
-   Bez plně důvěryhodné <xref:System.Security.Policy.StrongName> důkazy (třeba `MyComputer` legitimace zóny).  
  
-   Načíst do plně důvěryhodné <xref:System.AppDomain>.  
  
-   Načtené z umístění pod <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost, která <xref:System.AppDomain>.  
  
-   Není zpožděním.  
  
> [!NOTE]
>  Pokud funkce obejití jsou vypnuté pro všechny aplikace na počítači s použitím klíče registru, toto nastavení konfigurační soubor nemá žádný vliv. Další informace najdete v tématu [jak: Zákaz funkce obejití silného názvu](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak můžete určit chování, která ověřuje podpis silného názvu v plně důvěryhodné sestavení.  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Postupy: Zákaz funkce obejití silného názvu](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
