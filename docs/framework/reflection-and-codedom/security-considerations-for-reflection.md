---
title: "Důležité informace o zabezpečení pro reflexi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [.NET Framework], reflection
- MethodInfo parameters
- reflection, security
- partial trust,reflection
- nonpublic members
- reflection,partial trust
- link demands
ms.assetid: 42d9dc2a-8fcc-4ff3-b002-4ff260ef3dc5
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef0f9aac9222badb43e19c2901ff705485d5cf3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-for-reflection"></a>Důležité informace o zabezpečení pro reflexi
Reflexe umožňuje získat informace o typy a členy a členům přístup (to znamená, volání metod a konstruktory k získání a nastavení vlastnosti hodnoty, přidávat a odstraňovat obslužné rutiny událostí a tak dále). Použití reflexe ke získání informací o typy a členy není s omezeným přístupem. Všechny kódu můžete použít reflexe k provádění následujících úloh:  
  
-   Zobrazení výčtu typů a členů a prozkoumat jejich metadat.  
  
-   Zobrazení výčtu a prozkoumat sestavení a moduly.  
  
 Pomocí reflexe členům přístup, naopak podléhá omezením. Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]jen důvěryhodný kód můžete získat přístup kritické pro zabezpečení členů pomocí reflexe. Kromě toho můžete použít pouze důvěryhodný kód reflexe pro přístup k neveřejní členové, které by byly přímo přístupné pro zkompilovaný kód. Kód, který používá pro přístup ke členu kritická reflexi nakonec musí mít všechna oprávnění požadavky kritická člen jenom stejně jako u zkompilovaný kód.  
  
 Vztahují potřebná oprávnění můžete kód pomocí reflexe provádět následující typy přístupu:  
  
-   Veřejné členy přístupu, které nejsou kritické pro zabezpečení.  
  
-   Neveřejní členové přístupu, které by byly přístupné zkompilovaný kód, pokud nejsou tyto členy kritické pro zabezpečení. Příklady takových neveřejní členové:  
  
    -   Chráněné členy základní třídy volací kód. (V reflexe, to se označuje jako přístup na úrovni rodiny.)  
  
    -   `internal`členy (`Friend` členy v jazyce Visual Basic) v sestavení volací kód. (V reflexe, to se označuje jako přístup na úrovni sestavení.)  
  
    -   Soukromé členy jiné instancí třídy, která obsahuje kód volání.  
  
 Například kód, který běží v doméně aplikace v izolovaném prostoru je omezená pro přístup k popsané v tomto seznamu, pokud doména aplikace uděluje další oprávnění.  
  
 Od verze [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], pokusu o přístup k členů, které jsou obvykle nedostupné generuje o poskytnutí sady plus cílový objekt <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak. Kód, který je spuštěn s úplným vztahem důvěryhodnosti (například kód v aplikaci, která se spouští z příkazového řádku) může vždy splňovat tato oprávnění. (To je předmětem omezení přístupu ke kritické pro zabezpečení členů, jak je popsáno dále v tomto článku.)  
  
 Volitelně můžete udělit doméně aplikace v izolovaném prostoru s <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak, jak je popsáno v části [přístup k členy jestli jsou normálně nepřístupný](#accessingNormallyInaccessible)dál v tomto článku.  
  
<a name="accessingSecurityCritical"></a>   
## <a name="accessing-security-critical-members"></a>Přístup ke členům kritické pro zabezpečení  
 Člen je kritický pro zabezpečení má <xref:System.Security.SecurityCriticalAttribute>v případě, že patří do typu, který má <xref:System.Security.SecurityCriticalAttribute>, nebo pokud se nachází v kritické pro zabezpečení sestavení. Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], pravidla pro přístup ke členům kritické pro zabezpečení jsou následující:  
  
-   Kód transparentní nelze použít reflexe pro přístup ke členům kritické pro zabezpečení, i v případě, že je plně důvěryhodný kód. A <xref:System.MethodAccessException>, <xref:System.FieldAccessException>, nebo <xref:System.TypeAccessException> je vyvolána výjimka.  
  
-   Kód, který je spuštěn s částečnou důvěryhodností je považována za průhlednou.  
  
 Tato pravidla jsou stejné, ať už členem kritické pro zabezpečení přistupovat přímo pomocí zkompilovaný kód, nebo získat přístup prostřednictvím reflexe.  
  
 Spustí kód aplikace, který se spouští z příkazového řádku s úplným vztahem důvěryhodnosti. Tak dlouho, dokud není označena jako transparentní, může použít reflexe pro přístup k kritické pro zabezpečení členů. Spustíte-li stejný kód s částečnou důvěryhodností (například v doméně aplikace v izolovaném prostoru) je sestavení důvěryhodnosti úroveň určuje, jestli má přístup k kód kritický pro zabezpečení: Pokud sestavení se silným názvem a je nainstalována v globální mezipaměti sestavení, je důvěryhodné sestavení a můžete volat kritický pro zabezpečení členů. Pokud není důvěryhodný, bude transparentní, i když nebyla označena jako transparentní, a nemá přístup k kritické pro zabezpečení členů.  
  
 Další informace o modelu zabezpečení v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], najdete v části [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
## <a name="reflection-and-transparency"></a>Reflexe a průhlednosti  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], modul common language runtime určuje úroveň průhlednosti typu nebo člena z několika různými faktory, včetně úroveň důvěryhodnosti sestavení a úroveň důvěryhodnosti domény aplikace. Reflexe poskytuje <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Type.IsSecuritySafeCritical%2A>, a <xref:System.Type.IsSecurityTransparent%2A> vlastnosti, aby vám umožní zjistit úroveň průhlednosti typu. V následující tabulce jsou platné kombinace těchto vlastností.  
  
|Úroveň zabezpečení|IsSecurityCritical|IsSecuritySafeCritical|IsSecurityTransparent|  
|--------------------|------------------------|----------------------------|---------------------------|  
|Kritická|`true`|`false`|`false`|  
|Kritická|`true`|`true`|`false`|  
|Transparentní|`false`|`false`|`true`|  
  
 Pomocí těchto vlastností je mnohem jednodušší než zkoumání poznámky zabezpečení sestavení a typy jejího, kontrola aktuální úroveň důvěryhodnosti a pokus o duplicitní pravidla modulem runtime. Stejný typ může být například kritické pro zabezpečení při spuštění z příkazového řádku nebo transparentní pro zabezpečení při spuštění v doméně aplikace v izolovaném prostoru.  
  
 Nejsou k dispozici podobné vlastnosti na <xref:System.Reflection.MethodBase>, <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.Emit.TypeBuilder>, <xref:System.Reflection.Emit.MethodBuilder>, a <xref:System.Reflection.Emit.DynamicMethod> třídy. (Pro jiné reflexe a reflexe emitování abstrakce, atributů zabezpečení se použijí k související metody, například v případě vlastnosti, které se použijí k vlastnosti přistupující objekty.)  
  
<a name="accessingNormallyInaccessible"></a>   
## <a name="accessing-members-that-are-normally-inaccessible"></a>Přístup ke členům, které nejsou obvykle dostupné.  
 Chcete-li vyvolání členy, kteří jsou nedostupné podle pravidel usnadnění common language runtime pomocí reflexe, kódu musí poskytuje jedno z dvě oprávnění:  
  
-   Povolit kódu k vyvolání kteréhokoli člena neveřejní: váš kód musí mít udělena <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak.  
  
    > [!NOTE]
    >  Ve výchozím nastavení zásady zabezpečení odmítne toto oprávnění kód, který pochází z Internetu. Toto oprávnění měli udělit nikdy kód, který pochází z Internetu.  
  
-   Povolit k vyvolání kteréhokoli člena neveřejní tak dlouho, dokud grant sadu sestavení, které obsahuje Vyvolaný člen je stejný jako kód, nebo jsou podmnožinou, udělte sadu sestavení, které obsahuje, vyvolání code: váš kód musí mít udělena <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>příznak.  
  
 Předpokládejme například, udělte oprávnění Internet plus domény aplikace <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak a spusťte aplikaci Internet s dvě sestavení, A a B.  
  
-   Sestavení A můžete použít reflexe pro přístup k soukromé členy sestavení B, protože sada grant sestavení B nezahrnuje všechna oprávnění, která A nebylo uděleno.  
  
-   Sestavení A nemůže používat reflexe pro přístup k soukromé členy [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sestavení například mscorlib.dll, protože mscorlib.dll je plně důvěryhodný a proto má oprávnění, která nebyla udělena pro sestavení A. A <xref:System.MemberAccessException> se vyvolá, když zabezpečení přístupu kódu prochází zásobník za běhu.  
  
## <a name="serialization"></a>Serializace  
 Pro serializaci <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> příznak umožňuje získávat a nastavovat členy Serializovatelné typy, bez ohledu na usnadnění přístupu. Toto oprávnění umožňuje kódu ke zjištění a změnit privátní stav instance. (Kromě udělení příslušných oprávnění, musí být typ [označena](../../../docs/standard/attributes/applying-attributes.md) jako serializovatelný v metadatech.)  
  
## <a name="parameters-of-type-methodinfo"></a>Parametry typu MethodInfo  
 Vyhněte se zápis veřejné členy trvají <xref:System.Reflection.MethodInfo> parametry, zejména pro důvěryhodný kód. Takové členy může být zranitelnější vůči škodlivý kód. Zvažte například členem veřejné vysoce důvěryhodný kód, který přebírá <xref:System.Reflection.MethodInfo> parametr. Předpokládejme nepřímo volá veřejná člena <xref:System.Reflection.MethodBase.Invoke%2A> metodu na zadaný parametr. Pokud veřejný člen neprovádí kontroly nezbytná oprávnění, volání <xref:System.Reflection.MethodBase.Invoke%2A> metoda bude vždy úspěšné, protože systém zabezpečení určuje, že je volající vysoce důvěryhodný. I v případě, že škodlivý kód nemá oprávnění k přímo vyvolat metodu, je stále možné tak nepřímo voláním veřejného člena.  
  
## <a name="version-information"></a>Informace o verzi  
  
-   Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], pomocí reflexe nelze kód transparentní pro přístup ke členům kritické pro zabezpečení.  
  
-   <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> Příznak byla zavedená v [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)]. Starší verze [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] vyžadují <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak pro kód, který používá pro přístup k neveřejní členové reflexe. Toto je oprávnění, které se nikdy udělení částečně důvěryhodným kódem.  
  
-   Od verze [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], pomocí reflexe ke získání informací o neveřejní typy a členy nevyžaduje žádné oprávnění. V dřívějších verzích <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> příznak je požadovaná.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Permissions.ReflectionPermissionFlag>  
 <xref:System.Security.Permissions.ReflectionPermission>  
 <xref:System.Security.Permissions.SecurityPermission>  
 [Změny zabezpečení](../../../docs/framework/security/security-changes.md)  
 [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)  
 [Bezpečnostní problémy v generování reflexe](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 [Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [Použití atributů](../../../docs/standard/attributes/applying-attributes.md)  
 [Přístup k vlastním atributům](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)
