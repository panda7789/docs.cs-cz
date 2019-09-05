---
title: Element <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dd3105e573d40ae234ba7e122f20566911124d4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252542"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence – element >
Určuje, zda modul runtime <xref:System.Security.Policy.Publisher> vytvoří legitimaci pro zabezpečení přístupu kódu (CAS).  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<generatePublisherEvidence>**  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime <xref:System.Security.Policy.Publisher> vytvoří legitimaci.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|`false`|Nevytváří <xref:System.Security.Policy.Publisher> legitimace.|  
|`true`|Vytvoří <xref:System.Security.Policy.Publisher> legitimaci. Toto nastavení je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> V .NET Framework 4 a novějších, nemá tento prvek žádný vliv na časy načtení sestavení. Další informace najdete v části "zjednodušení zásad zabezpečení" v článku [změny zabezpečení](../../../security/security-changes.md).  
  
 Modul CLR (Common Language Runtime) se pokusí ověřit podpis Authenticode v době načítání a vytvořit <xref:System.Security.Policy.Publisher> legitimaci pro sestavení. Ve výchozím nastavení ale většina aplikací nepotřebuje <xref:System.Security.Policy.Publisher> důkazy. Standardní zásady CAS nezávisí na <xref:System.Security.Policy.PublisherMembershipCondition>. Měli byste se vyhnout zbytečnému počátečnímu nákladům souvisejícím s ověřováním podpisu vydavatele, pokud vaše aplikace neběží na počítači s vlastními zásadami CAS, nebo má v <xref:System.Security.Permissions.PublisherIdentityPermission> úmyslu splňovat požadavky pro prostředí s částečnou důvěryhodností. (Požadavky na oprávnění identity jsou vždycky úspěšné v prostředí s plnou důvěryhodností.)  
  
> [!NOTE]
> Pro zlepšení výkonu při spouštění doporučujeme `<generatePublisherEvidence>` , aby služby používaly tento prvek.  Použití tohoto prvku může také pomoci zabránit prodlevám, které mohou způsobit časový limit a zrušení spuštění služby.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít pouze v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `<generatePublisherEvidence>` element k zakázání kontroly zásad vydavatele CAS pro aplikaci.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
