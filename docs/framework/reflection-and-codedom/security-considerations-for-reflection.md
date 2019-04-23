---
title: Důležité informace o zabezpečení pro reflexi
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], reflection
- MethodInfo parameters
- reflection, security
- partial trust,reflection
- nonpublic members
- reflection,partial trust
- link demands
ms.assetid: 42d9dc2a-8fcc-4ff3-b002-4ff260ef3dc5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c238f0aebd7c81443eb55fe0ee84844f0c9aee8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207510"
---
# <a name="security-considerations-for-reflection"></a>Důležité informace o zabezpečení pro reflexi
Reflexe umožňuje získat informace o typech a členech a chcete získat přístup ke členům (to znamená pro volání metody a konstruktory, k získání a nastavení vlastností hodnoty, přidávat a odebírat obslužné rutiny událostí a tak dále). Použití reflexe získat informace o typech a členech není omezeno. Veškerý kód, můžete použít reflexe provádět následující úlohy:  
  
-   Zobrazení výčtu typů a členů a zkontrolovat jejich metadat.  
  
-   Zobrazení výčtu a prozkoumejte sestavení a modulů.  
  
 Pomocí operace reflection přístupu k členům, naopak podléhá omezením. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], jen pro důvěryhodného kódu můžete použít reflexe pro přístup ke členům kritické pro zabezpečení. Kromě toho můžete použít pouze pro důvěryhodného kódu reflexe pro přístup k neveřejné členy, které by byly přímo přístupné pro zkompilovaný kód. Kód, který se používá pro přístup ke členu bezpečný a kritický reflexi a konečně, musí mít oprávnění bezpečný a kritický člen požadavky, stejně jako u zkompilovaný kód.  
  
 V souladu s potřebnými oprávněními můžete kód pomocí reflexe provádět následující typy přístupu:  
  
-   Přístup k veřejné členy, které nejsou kritické pro zabezpečení.  
  
-   Přístup k neveřejné členy, které by byly přístupné pro zkompilovaný kód, pokud nejsou členy kritické z hlediska zabezpečení. Příklady takových neveřejní členové:  
  
    -   Chráněné členy základní třídy volající kód. (V reflexi, označuje se jako řady úrovně přístupu.)  
  
    -   `internal` Členové (`Friend` v jazyce Visual Basic) v sestavení volajícího kódu. (V reflexi, to se označuje jako přístup na úrovni sestavení.)  
  
    -   Soukromé členy instancí jiné třídy, která obsahuje volající kód.  
  
 Například kód, který běží v doméně aplikace v izolovaném prostoru je omezený přístup k popsané v tomto seznamu, pokud doména aplikace zaručuje další oprávnění.  
  
 Počínaje [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], pokus o přístup ke členům, které jsou obvykle nedostupná generuje poptávka sady udělení plus cílového objektu <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak. Kód, který je spuštěn s úplným vztahem důvěryhodnosti (například kód v aplikaci, která se spustí z příkazového řádku) můžete vždy splňovat tato oprávnění. (To je v souladu s omezeními v přístupu k členům kritické pro zabezpečení, jak je popsáno dále v tomto článku.)  
  
 Volitelně můžete udělit doméně aplikace v izolovaném prostoru <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak, jak je popsáno v části [přístup k členům, že jsou obvykle nedostupná](#accessingNormallyInaccessible)dále v tomto článku.  
  
<a name="accessingSecurityCritical"></a>   
## <a name="accessing-security-critical-members"></a>Přístup k členům kritické pro zabezpečení  
 Člen je kritický pro zabezpečení má-li <xref:System.Security.SecurityCriticalAttribute>, pokud patří do typem, který má <xref:System.Security.SecurityCriticalAttribute>, nebo pokud je v kritické pro zabezpečení sestavení. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], pravidla pro přístup k členům kritické pro zabezpečení jsou následující:  
  
-   Transparentní kód nemůže použít reflexe pro přístup ke členům kritické pro zabezpečení, i v případě, že je plně důvěryhodný kód. A <xref:System.MethodAccessException>, <xref:System.FieldAccessException>, nebo <xref:System.TypeAccessException> je vyvolána výjimka.  
  
-   Kód, který běží s částečnou důvěryhodností je považována za průhlednou.  
  
 Tato pravidla jsou stejné, ať už členem kritické pro zabezpečení k němu přistupuje přímo zkompilovaný kód, nebo přistupovat pomocí reflexe.  
  
 Spustí kód aplikace, která se spouští z příkazového řádku s úplným vztahem důvěryhodnosti. Tak dlouho, dokud není označena jako transparentní, může použít reflexe pro přístup ke členům kritické pro zabezpečení. Při spuštění stejný kód s částečnou důvěryhodností (například v doméně aplikace v izolovaném prostoru) úroveň důvěryhodnosti sestavení určuje, jestli můžete přistupovat k kritické pro zabezpečení kódu: Pokud sestavení se silným názvem a je nainstalováno v globální mezipaměti sestavení, je důvěryhodná sestavení a může volat členy kritické z hlediska zabezpečení. Pokud není důvěryhodný, bude transparentní, i když nebyl označen jako transparentní, a nebude moct přistupovat k členy kritické z hlediska zabezpečení.  
  
 Další informace o modelu zabezpečení v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], naleznete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
## <a name="reflection-and-transparency"></a>Reflexi a průhlednosti  
 Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], modul common language runtime určuje úroveň průhlednosti typu nebo člena z několika různými faktory, včetně úroveň důvěryhodnosti sestavení a úroveň důvěryhodnosti domény aplikace. Poskytuje reflexe <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Type.IsSecuritySafeCritical%2A>, a <xref:System.Type.IsSecurityTransparent%2A> vlastnosti vám umožní zjistit úroveň průhlednosti typu. V následující tabulce jsou uvedeny platné kombinace těchto vlastností.  
  
|Úroveň zabezpečení|IsSecurityCritical|IsSecuritySafeCritical|IsSecurityTransparent|  
|--------------------|------------------------|----------------------------|---------------------------|  
|Kritická|`true`|`false`|`false`|  
|Bezpečný a kritický|`true`|`true`|`false`|  
|Transparentní|`false`|`false`|`true`|  
  
 Pomocí těchto vlastností je mnohem jednodušší než zkoumání poznámky k zabezpečení sestavení a jeho typy, kontrola aktuální úroveň důvěryhodnosti a pokusu duplikovat pravidla modul runtime. Pro stejný typ může být například kritické pro zabezpečení při spuštění z příkazového řádku, nebo transparentní pro zabezpečení při spuštění v doméně aplikace v izolovaném prostoru.  
  
 Na jsou podobné vlastnosti <xref:System.Reflection.MethodBase>, <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.Emit.TypeBuilder>, <xref:System.Reflection.Emit.MethodBuilder>, a <xref:System.Reflection.Emit.DynamicMethod> třídy. (Pro další reflexe a reflexe abstrakce generování, atributy zabezpečení jsou použity na související metody, například v případě vlastnosti, které se použijí pro přistupující objekty vlastnosti.)  
  
<a name="accessingNormallyInaccessible"></a>   
## <a name="accessing-members-that-are-normally-inaccessible"></a>Přístup k členům, které jsou obvykle nedostupná  
 Používat reflexi k vyvolání členy, které budou pro podle pravidel usnadnění modulu common language runtime, váš kód musí být uděleno jednu z dvou oprávnění:  
  
-   Chcete-li povolit kód, který má být vyvolán libovolný neveřejný člen: váš kód musí být uděleno <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak.  
  
    > [!NOTE]
    >  Ve výchozím nastavení zásady zabezpečení zakazuje toto oprávnění pro kód, který pochází z Internetu. Toto oprávnění musí udělit nikdy kód, který pochází z Internetu.  
  
-   Povolit kódu k vyvolání neveřejný člen, za předpokladu, sady udělení sestavení, které obsahuje Vyvolaný člen je stejná jako nebo podmnožinu, že sada oprávnění udělená sestavení, která obsahuje kód vyvolání: Váš kód musí být uděleno <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak.  
  
 Předpokládejme například, že udělíte doménu aplikace Internetová oprávnění plus <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznak a pak spusťte aplikaci Internet se dvě sestavení, A a B.  
  
-   Sestavení A můžete použít reflexe pro přístup ke členům soukromé sestavení B, protože sada udělení sestavení B nezahrnuje všechna oprávnění, která A nebylo uděleno.  
  
-   Sestavení A nelze použít reflexe pro přístup k privátní členy [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sestavení, jako například mscorlib.dll, protože soubor mscorlib.dll je plně důvěryhodný a proto má oprávnění, která nebyla udělena sestavení A. A <xref:System.MemberAccessException> je vyvolána při zabezpečení přístupu kódu vás zásobníku za běhu.  
  
## <a name="serialization"></a>Serializace  
 Pro serializaci <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> příznak umožňuje získávat a nastavovat členy Serializovatelné typy, bez ohledu na přístupnost. Toto oprávnění umožňuje kódu ke zjištění a privátní stav instance změnit. (Kromě udělením příslušná oprávnění, musí být typu [označené](../../../docs/standard/attributes/applying-attributes.md) v metadatech jako serializovatelný.)  
  
## <a name="parameters-of-type-methodinfo"></a>Parametry typu MethodInfo  
 Vyhněte se vytváření veřejné členy trvají <xref:System.Reflection.MethodInfo> parametry, zejména pro důvěryhodného kódu. Tito členové můžou být zranitelnější vůči škodlivý kód. Představte si třeba veřejného člena v vysoce důvěryhodným kódem, který přijímá <xref:System.Reflection.MethodInfo> parametru. Předpokládejme, že veřejný člen nepřímo volá <xref:System.Reflection.MethodBase.Invoke%2A> metodu na zadaný parametr. Pokud veřejný člen neprovádí kontroly nezbytná oprávnění, volání <xref:System.Reflection.MethodBase.Invoke%2A> – metoda bude vždy úspěšné, protože systém zabezpečení určuje, že je vysoce důvěryhodné volající. I v případě, že škodlivý kód nemá oprávnění k přímo vyvolat metodu, můžete stále provádět tak nepřímo voláním veřejný člen.  
  
## <a name="version-information"></a>Informace o verzi  
  
-   Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], transparentní kód nemůže použít reflexe pro přístup ke členům kritické pro zabezpečení.  
  
-   <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> Příznak se používá v [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)]. Starší verze [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] vyžadují <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak pro kód, který se používá pro přístup k neveřejné členy reflexe. Toto je oprávnění, které nikdy udělení částečně důvěryhodným kódem.  
  
-   Počínaje [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], pomocí operace reflection k získání informací o neveřejným typům a členům nevyžaduje žádná oprávnění. V dřívějších verzích <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> příznak je povinný.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Permissions.ReflectionPermissionFlag>
- <xref:System.Security.Permissions.ReflectionPermission>
- <xref:System.Security.Permissions.SecurityPermission>
- [Změny zabezpečení](../../../docs/framework/security/security-changes.md)
- [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)
- [Bezpečnostní problémy v generování reflexe](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)
- [Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Použití atributů](../../../docs/standard/attributes/applying-attributes.md)
- [Přístup k vlastním atributům](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)
