---
title: Používání knihoven z částečně důvěryhodného kódu
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8500abe590d4c85dcb5ecda54212a1ba9cc7950d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586990"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Používání knihoven z částečně důvěryhodného kódu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  Toto téma řeší chování sestavení se silným názvem a platí jenom pro [úrovně 1](../../../docs/framework/misc/security-transparent-code-level-1.md) sestavení. [Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md) sestavení v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] nebo později nejsou ovlivněny silných názvů. Další informace o změnách systém zabezpečení najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
 Aplikace, které přijímají menší než úplný vztah důvěryhodnosti z jejich hostitele nebo izolovaného prostoru není povoleno volat sdílených knihoven spravovaných, pokud jim prostřednictvím zapisovače knihovny konkrétně umožňuje <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut. Uživatelé vytvářející obsah aplikace proto musí být vědomi, že některé knihovny nebudou k dispozici k nim z částečně důvěryhodného kontextu. Ve výchozím nastavení, veškerý kód, který se spustí v částečným vztahem důvěryhodnosti [izolovaného prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) a není v seznamu sestavení úplné důvěryhodnosti je částečně důvěryhodné. Pokud neočekáváte váš kód, který se spustí z částečně důvěryhodného kontextu nebo volat částečně důvěryhodným kódem, není nutné mít obavy o informace v této části. Ale pokud píšete kód, který musí spolupracovat s částečně důvěryhodným kódem nebo provoz z částečně důvěryhodného kontextu, je třeba zvážit následující faktory:  
  
- Knihovny musí být podepsané silným názvem, aby bylo možné sdílet mezi více aplikacemi. Silné názvy umožňují váš kód umístěn v globální mezipaměti sestavení, nebo se přidá do seznamu úplné důvěryhodnosti izolace (sandbox) <xref:System.AppDomain>, a umožňují uživatelům ověřit, že konkrétní mobilní kód ve skutečnosti pochází od vás.  
  
- Ve výchozím nastavení, silným názvem [úrovně 1](../../../docs/framework/misc/security-transparent-code-level-1.md) sdílené knihovny provést implicitní [LinkDemand](../../../docs/framework/misc/link-demands.md) úplného vztahu důvěryhodnosti automaticky, bez zapisovač knihovny museli něco dělat.  
  
- Pokud volající nemá úplný vztah důvěryhodnosti, ale přesto pokusí o volání takové knihovny, modul runtime vyvolá <xref:System.Security.SecurityException> a volající nemá povoleno propojit do knihovny.  
  
- Aby bylo možné zakázat automatické **LinkDemand** a zabránit výjimky vyvolané, můžete umístit **AllowPartiallyTrustedCallersAttribute** atribut v oboru sestavení sdílené Knihovna. Tento atribut umožňuje volat z částečně důvěryhodného kódu spravované knihovny.  
  
- Částečně důvěryhodným kódem, které je udělen přístup k knihovnu se tento atribut je pořád v souladu s další omezení, které jsou definované <xref:System.AppDomain>.  
  
- Neexistuje žádný programový způsob, jak částečně důvěryhodným kódem pro volání knihovny, který nemá **AllowPartiallyTrustedCallersAttribute** atribut.  
  
 Knihovny, které jsou privátní pro konkrétní aplikace nevyžadují silným názvem nebo **AllowPartiallyTrustedCallersAttribute** atribut a nemůže být odkazován potenciálně škodlivý kód mimo aplikaci. Takový kód je chráněn proti zneužití úmyslnému i neúmyslnému částečně důvěryhodným kódem mobilní bez developer by bylo nutné dělat nic navíc.  
  
 Měli byste zvážit explicitně povoluje použití částečně důvěryhodným kódem pro následující typy kódu:  
  
- Kód, který byl testován usilovně pro chyby zabezpečení a je v souladu s pokyny, podle [zabezpečené kódování zásady](../../../docs/standard/security/secure-coding-guidelines.md).  
  
- Knihovny kódu se silným názvem, které jsou určeny konkrétně pro částečně důvěryhodným scénáře.  
  
- Všechny součásti (ať už částečně nebo zcela důvěryhodných) podepsanému pomocí silného názvu, který bude volán kód, který se stáhne z Internetu.  
  
> [!NOTE]
>  Některé třídy v knihovně tříd rozhraní .NET Framework nemají **AllowPartiallyTrustedCallersAttribute** atribut a nemůže být volán částečně důvěryhodným kódem.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)
