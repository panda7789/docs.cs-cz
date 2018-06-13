---
title: '&lt;generatePublisherEvidence&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f56bbef6ed6decf6be4246f649665db4cf0f766
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746017"
---
# <a name="ltgeneratepublisherevidencegt-element"></a>&lt;generatePublisherEvidence&gt; – Element
Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> důkaz pro zabezpečení přístupu kódu (CAS).  
  
 \<Konfigurace >  
\<modul runtime >  
\<generatePublisherEvidence >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> důkaz.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Nevytváří <xref:System.Security.Policy.Publisher> důkaz.|  
|`true`|Vytvoří <xref:System.Security.Policy.Publisher> důkaz. Toto nastavení je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  V [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] a později tento element nemá žádný vliv na časů načtení sestavení. Další informace najdete v části "Zjednodušení zásad zabezpečení" v [změny zabezpečení](../../../../../docs/framework/security/security-changes.md).  
  
 Modul CLR (CLR) pokusí se ověřit podpis Authenticode při načítání, chcete-li vytvořit <xref:System.Security.Policy.Publisher> důkaz pro sestavení. Nicméně ve výchozím nastavení, většina aplikací není nutné <xref:System.Security.Policy.Publisher> důkaz. Standardní zásady certifikační Autority na nespoléhá se <xref:System.Security.Policy.PublisherMembershipCondition>. Neměli byste nepotřebné spuštění náklady spojené s ověření podpisu vydavatele, pokud vaše aplikace spustí na počítači s vlastní zásadu CAS nebo je hodláte splňují požadavky pro <xref:System.Security.Permissions.PublisherIdentityPermission> v prostředí s částečným vztahem důvěryhodnosti. (Požadavky pro oprávnění identity vždy úspěšné v prostředí plné důvěryhodnosti.)  
  
> [!NOTE]
>  Doporučujeme, který služeb pomocí `<generatePublisherEvidence>` elementu, který chcete zvýšit výkon při spouštění.  Pomocí tohoto elementu může také pomoci zabránit zpoždění, které může způsobit, že vypršení časového limitu a zrušení spuštění služby.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element může použít pouze v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<generatePublisherEvidence>` elementu, který chcete zakázat zjišťování certifikační Autority zásad vydavatele pro aplikaci.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
