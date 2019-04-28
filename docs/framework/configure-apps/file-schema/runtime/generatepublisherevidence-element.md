---
title: Element <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09a12f062b2fe3ad6e5ac90f0d268bbbeab44876
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674139"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> Element
Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> důkazy pro zabezpečení přístupu kódu (CAS).  
  
 \<Konfigurace >  
\<modul runtime >  
\<generatePublisherEvidence>  
  
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
|`false`|Nevytváří žádné <xref:System.Security.Policy.Publisher> důkaz.|  
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
>  V [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] a později, tento element nemá žádný vliv na dobu načítání sestavení. Další informace najdete v části "Zjednodušení zásady zabezpečení" v [změny zabezpečení](../../../../../docs/framework/security/security-changes.md).  
  
 Modul CLR (CLR) pokusí o ověření podpisu Authenticode v okamžiku načtení vytvořit <xref:System.Security.Policy.Publisher> legitimaci sestavení. Ale ve výchozím nastavení, většina aplikací není nutné <xref:System.Security.Policy.Publisher> důkaz. Standardní zásady CAS nespoléhá na <xref:System.Security.Policy.PublisherMembershipCondition>. Měli byste se vyhnout zbytečným spuštění náklady spojené s ověření podpisu vydavatele, pokud vaše aplikace spustí na počítači s vlastní zásady CAS nebo hodlá splňovat požadavky pro <xref:System.Security.Permissions.PublisherIdentityPermission> v prostředí s částečným vztahem důvěryhodnosti. (Požadavky na identity oprávnění vždy úspěšné v prostředí úplného vztahu důvěryhodnosti.)  
  
> [!NOTE]
>  Doporučujeme vám, které služby použijte `<generatePublisherEvidence>` elementu, chcete-li zlepšit výkon při spuštění.  Použití tohoto prvku může také pomoct vyhnout se prodlevám, které může způsobit vypršení časového limitu a zrušení spuštění služby.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít pouze v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<generatePublisherEvidence>` prvek, který chcete zakázat kontrolu pro certifikační Autority zásad vydavatele aplikace.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
