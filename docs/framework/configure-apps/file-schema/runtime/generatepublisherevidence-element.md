---
title: Element <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645348"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> Element
Určuje, zda runtime <xref:System.Security.Policy.Publisher> vytvoří důkazy pro zabezpečení přístupu kódu (CAS).  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda soubor <xref:System.Security.Policy.Publisher> runtime vytvoří důkazy.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Nevytváří <xref:System.Security.Policy.Publisher> důkazy.|  
|`true`|Vytváří <xref:System.Security.Policy.Publisher> důkazy. Toto nastavení je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> V rozhraní .NET Framework 4 a novější tento prvek nemá žádný vliv na doby načítání sestavení. Další informace naleznete v části Zjednodušení zásad zabezpečení v části [Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Běžný jazyk runtime (CLR) se pokusí ověřit podpis Authenticode v době načítání k vytvoření <xref:System.Security.Policy.Publisher> legitimace pro sestavení. Ve výchozím nastavení však většina aplikací nepotřebujete <xref:System.Security.Policy.Publisher> důkazy. Standardní zásady CAS nezávisí na <xref:System.Security.Policy.PublisherMembershipCondition>. Měli byste se vyhnout zbytečným nákladům na spuštění spojeným s ověřením podpisu vydavatele, pokud se <xref:System.Security.Permissions.PublisherIdentityPermission> aplikace nespustí v počítači s vlastními zásadami CAS nebo pokud nemá v úmyslu uspokojit požadavky v prostředí s částečnou důvěryhodností. (Požadavky na oprávnění identity vždy úspěšné v prostředí s plnou důvěryhodností.)  
  
> [!NOTE]
> Doporučujeme, aby `<generatePublisherEvidence>` služby používat prvek ke zlepšení výkonu při spuštění.  Pomocí tohoto prvku můžete také pomoci vyhnout se zpoždění, které může způsobit časový odčasový čas a zrušení spuštění služby.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento prvek lze použít pouze v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak `<generatePublisherEvidence>` pomocí prvku zakázat kontrolu zásad vydavatele CAS pro aplikaci.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení běhu](index.md)
- [Schéma konfiguračního souboru](../index.md)
