---
title: Důležité informace o zabezpečení pro reflexi
description: Přečtěte si o požadavcích na zabezpečení pro reflexi v .NET. Získání informací o typech a členech je povoleno, ale přístup k členům má omezení.
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
ms.openlocfilehash: 0465cbd5ceb7d4f44bb6d10865fcbd17b8ed7af6
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865252"
---
# <a name="security-considerations-for-reflection"></a>Důležité informace o zabezpečení pro reflexi

Reflexe poskytuje možnost získat informace o typech a členech a získat přístup ke členům (to znamená volat metody a konstruktory, získat a nastavit hodnoty vlastností, přidat a odebrat obslužné rutiny události atd.). Použití reflexe k získání informací o typech a členech není omezeno. Veškerý kód může pomocí reflexe provádět následující úlohy:

- Zobrazení výčtu typů a členů a kontrola jejich metadat.

- Zobrazení výčtu a kontrola sestavení a modulů.

Použití reflexe pro přístup ke členům naproti tomu závisí na omezeních. Počínaje .NET Framework 4 může k přístupu ke členům kritickým pro zabezpečení použít reflexi jenom důvěryhodný kód. Kromě toho může použití reflexe k přístupu k NonPublic členům, kteří by nemuseli být přímým přístupem k kompilovanému kódu, použít pouze důvěryhodný kód. Nakonec kód, který používá reflexi pro přístup k bezpečnému členu kritického typu, musí mít libovolné oprávnění, aby Nepostradatelně kritické členské požadavky, stejně jako u zkompilovaného kódu.

V souladu s potřebnými oprávněními může kód pomocí reflexe provádět následující typy přístupu:

- Přístup k veřejným členům, kteří nejsou kritické pro zabezpečení

- Přístup ke členům NonPublic, které by byly přístupné zkompilovanému kódu, pokud tyto členy nejsou kritické pro zabezpečení. Příklady takových členů NonPublic zahrnují:

  - Chránění členové základních tříd kódu volání. (V reflexi se označuje jako přístup na úrovni rodiny.)

  - `internal`Členové ( `Friend` Členové v Visual Basic) v sestavení volajícího kódu. (V reflexi se označuje jako přístup na úrovni sestavení.)

  - Soukromé členy třídy, která obsahuje volající kód.

Například kód, který je spuštěn v doméně aplikace v izolovaném prostoru, je omezený na přístup popsaný v tomto seznamu, pokud aplikační doména neuděluje další oprávnění.

Od .NET Framework 2,0 s aktualizací Service Pack 1 se snaží získat přístup ke členům, které jsou normálně nepřístupné, vygeneruje poptávku pro sadu udělení cílového objektu a <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznakem. Kód, který je spuštěn s úplným vztahem důvěryhodnosti (například kód v aplikaci spouštěný z příkazového řádku), může vždy splňovat tato oprávnění. (Toto je v souladu s omezeními při přístupu ke členům kritickým pro zabezpečení, jak je popsáno dále v tomto článku.)

Volitelně může aplikační doména s izolovaným prostorem (sandbox) přidělit <xref:System.Security.Permissions.ReflectionPermission> s <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznakem, jak je popsáno v části [přístup ke členům, kteří jsou normálně nepřístupní](#accessingNormallyInaccessible), dále v tomto článku.

<a name="accessingSecurityCritical"></a>

## <a name="accessing-security-critical-members"></a>Přístup ke členům kritickým pro zabezpečení

Člen je kritický pro zabezpečení, pokud má <xref:System.Security.SecurityCriticalAttribute> , pokud má, pokud patří do typu, který má <xref:System.Security.SecurityCriticalAttribute> , nebo pokud je v sestavení kritickém pro zabezpečení. Počínaje .NET Framework 4 jsou pravidla pro přístup ke členům kritickým pro zabezpečení následující:

- Transparentní kód nemůže použít reflexi pro přístup ke členům kritickým pro zabezpečení i v případě, že kód je plně důvěryhodný. <xref:System.MethodAccessException> <xref:System.FieldAccessException> <xref:System.TypeAccessException> Je vyvolána výjimka, nebo.

- Kód, který je spuštěn s částečnou důvěryhodností, je považován za transparentní.

Tato pravidla jsou stejná, bez ohledu na to, zda je ke kritickému členovi zabezpečení přistupuje přímo kompilovaným kódem, nebo k němu lze použít reflex

Kód aplikace spouštěný z příkazového řádku se spouští s úplným vztahem důvěryhodnosti. Pokud není označený jako transparentní, může k přístupu ke členům kritickým pro zabezpečení použít reflexi. Když je stejný kód spuštěn s částečným vztahem důvěryhodnosti (například v doméně aplikace v izolovaném prostoru), určuje úroveň vztahu důvěryhodnosti sestavení, zda může získat přístup ke kódu kritickému pro zabezpečení: Pokud sestavení má silný název a je nainstalováno v globální mezipaměti sestavení (GAC), jedná se o důvěryhodné sestavení a může volat členy kritické pro zabezpečení. Pokud není důvěryhodná, je tato volba transparentní, i když nebyla označena jako průhledná a nemůže přistupovat ke členům kritickým pro zabezpečení.

Další informace o modelu zabezpečení v .NET Framework 4 najdete v tématu [změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).

## <a name="reflection-and-transparency"></a>Odraz a průhlednost

Počínaje .NET Framework 4 určuje modul CLR (Common Language Runtime) úroveň transparentnosti typu nebo člena z několika faktorů, včetně úrovně důvěryhodnosti sestavení a úrovně důvěryhodnosti domény aplikace. Reflexe <xref:System.Type.IsSecurityCritical%2A> poskytuje <xref:System.Type.IsSecuritySafeCritical%2A> vlastnosti, a, <xref:System.Type.IsSecurityTransparent%2A> které umožňují zjistit úroveň transparentnosti daného typu. V následující tabulce jsou uvedeny platné kombinace těchto vlastností.

|Úroveň zabezpečení|IsSecurityCritical|IsSecuritySafeCritical|IsSecurityTransparent|
|--------------------|------------------------|----------------------------|---------------------------|
|Kritické|`true`|`false`|`false`|
|Bezpečné – kritické|`true`|`true`|`false`|
|Průhlednost|`false`|`false`|`true`|

Použití těchto vlastností je mnohem jednodušší než zkoumání poznámek zabezpečení sestavení a jeho typů, kontroly aktuální úrovně vztahu důvěryhodnosti a pokusu o duplikaci pravidel modulu runtime. Například stejný typ může být kritický pro zabezpečení při spuštění z příkazového řádku nebo transparentní z hlediska zabezpečení při spuštění v doméně aplikace v izolovaném prostoru.

Existují podobné vlastnosti <xref:System.Reflection.MethodBase> <xref:System.Reflection.FieldInfo> tříd,,, a <xref:System.Reflection.Emit.TypeBuilder> <xref:System.Reflection.Emit.MethodBuilder> <xref:System.Reflection.Emit.DynamicMethod> . (Pro další abstrakce vysílané abstrakce a atributy zabezpečení jsou aplikovány na přidružené metody, například v případě vlastností, které jsou aplikovány na přistupující objekty vlastnosti.)

<a name="accessingNormallyInaccessible"></a>

## <a name="accessing-members-that-are-normally-inaccessible"></a>Přístup ke členům, kteří jsou obvykle nepřístupné

Chcete-li použít reflexi k vyvolání členů, kteří nejsou k dispozici v souladu s pravidly přístupnosti společného jazykového modulu runtime, musí být vašemu kódu udělena jedna ze dvou oprávnění:

- Chcete-li kódu dovolit vyvolat libovolný NonPublic člen: váš kód musí být udělen <xref:System.Security.Permissions.ReflectionPermission> pomocí <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznaku.

  > [!NOTE]
  > Ve výchozím nastavení zásady zabezpečení zamítne toto oprávnění ke kódu, který pochází z Internetu. Toto oprávnění by nikdy nemělo být uděleno kódu, který pochází z Internetu.

- Chcete-li povolit, aby kód vyvolal libovolný NonPublic člen, pokud sada udělení sestavení, která obsahuje vyvolaný člen, je stejná jako nebo podmnožina sady, sada udělení sestavení, která obsahuje vyvolání kódu: váš kód musí být udělen <xref:System.Security.Permissions.ReflectionPermission> pomocí <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> příznaku.

Předpokládejme například, že udělíte přístupová oprávnění k doméně aplikace <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a k příznaku a potom spustíte internetovou aplikaci se dvěma sestaveními, a a B.

- Sestavení A může použít reflexi pro přístup k soukromým členům sestavení B, protože udělení sady sestavení B nezahrnuje žádná oprávnění, která nebyla udělena.

- Sestavení A nemůže použít reflexi pro přístup k soukromým členům .NET Frameworkch sestavení, jako je například mscorlib.dll, protože mscorlib.dll je plně důvěryhodná, a proto má oprávnění, která nebyla udělena sestavení A. <xref:System.MemberAccessException>Výjimka je vyvolána, když zabezpečení přístupu kódu projde zásobník v době běhu.

## <a name="serialization"></a>Serializace

Pro serializaci <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> příznakem poskytuje možnost získat a nastavit členy serializovatelných typů bez ohledu na přístupnost. Toto oprávnění umožňuje kódu zjistit a změnit soukromý stav instance. (Kromě udělení příslušných oprávnění musí být typ [označen](../../standard/attributes/applying-attributes.md) jako serializovatelný v metadatech.)

## <a name="parameters-of-type-methodinfo"></a>Parametry typu MethodInfo

Vyhněte se psaní veřejných členů, kteří přijímají <xref:System.Reflection.MethodInfo> parametry, zejména pro důvěryhodný kód. Tito členové můžou být zranitelní proti škodlivému kódu. Představte si třeba veřejný člen ve vysoce důvěryhodném kódu, který přijímá <xref:System.Reflection.MethodInfo> parametr. Předpokládat, že veřejný člen nepřímo volá <xref:System.Reflection.MethodBase.Invoke%2A> metodu pro zadaný parametr. Pokud veřejný člen neprovede potřebné kontroly oprávnění, volání <xref:System.Reflection.MethodBase.Invoke%2A> metody bude vždy úspěšné, protože systém zabezpečení určí, že volající je vysoce důvěryhodný. I v případě, že škodlivý kód nemá oprávnění k přímému vyvolání metody, může i nadále provádět nepřímo voláním veřejného člena.

## <a name="version-information"></a>Informace o verzi

- Počínaje .NET Framework 4, transparentní kód nemůže použít reflexi pro přístup ke členům kritickým pro zabezpečení.

- <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>Příznak je představený v sadě .NET Framework 2,0 Service Pack 1. Starší verze .NET Framework vyžadují <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> příznak kódu, který používá reflexi pro přístup ke členům NonPublic. Toto je oprávnění, které by nikdy nemělo být uděleno částečně důvěryhodnému kódu.

- Počínaje .NET Framework 2,0, použití reflexe k získání informací o typech a členech NonPublic nevyžaduje žádná oprávnění. V dřívějších verzích se <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> příznak vyžaduje.

## <a name="see-also"></a>Viz také

- <xref:System.Security.Permissions.ReflectionPermissionFlag>
- <xref:System.Security.Permissions.ReflectionPermission>
- <xref:System.Security.Permissions.SecurityPermission>
- [Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
- [Zabezpečení přístupu kódu](../misc/code-access-security.md)
- [Bezpečnostní problémy v generování reflexe](security-issues-in-reflection-emit.md)
- [Zobrazení informací o typu](viewing-type-information.md)
- [Použití atributů](../../standard/attributes/applying-attributes.md)
- [Přístup k vlastním atributům](accessing-custom-attributes.md)
