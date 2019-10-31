---
title: Element <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: b04ef53d6e9c3d954b0925ea8634b3d220b36af7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116575"
---
# <a name="generatepublisherevidence-element"></a>\<element > generatePublisherEvidence
Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> legitimace pro zabezpečení přístupu kódu (CAS).  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<generatePublisherEvidence >**  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> legitimace.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Nevytváří <xref:System.Security.Policy.Publisher> legitimace.|  
|`true`|Vytvoří legitimaci <xref:System.Security.Policy.Publisher>. Toto nastavení je výchozí.|  
  
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
  
 Modul CLR (Common Language Runtime) se pokusí ověřit podpis Authenticode v době načítání a vytvořit <xref:System.Security.Policy.Publisher> legitimaci pro sestavení. Ve výchozím nastavení ale většina aplikací nepotřebuje <xref:System.Security.Policy.Publisher> legitimace. Standardní zásady CAS nespoléhají na <xref:System.Security.Policy.PublisherMembershipCondition>. Měli byste se vyhnout zbytečnému počátečnímu nákladům souvisejícím s ověřováním podpisu vydavatele, pokud se vaše aplikace nespustí na počítači s vlastními zásadami CAS, nebo má za následek splnění požadavků pro <xref:System.Security.Permissions.PublisherIdentityPermission> v prostředí s částečným vztahem důvěryhodnosti. (Požadavky na oprávnění identity jsou vždycky úspěšné v prostředí s plnou důvěryhodností.)  
  
> [!NOTE]
> Pro zlepšení výkonu při spuštění doporučujeme, aby služby používaly `<generatePublisherEvidence>` element.  Použití tohoto prvku může také pomoci zabránit prodlevám, které mohou způsobit časový limit a zrušení spuštění služby.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít pouze v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí elementu `<generatePublisherEvidence>` zakázat kontrolu zásad vydavatele CAS pro aplikaci.  
  
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
