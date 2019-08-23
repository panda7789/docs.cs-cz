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
ms.openlocfilehash: e08cb1b3f4708b4314f0cd663f70fa10aaa1aded
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910683"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Používání knihoven z částečně důvěryhodného kódu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> Toto téma řeší chování sestavení se silným názvem a vztahuje se pouze na sestavení [úrovně 1](../../../docs/framework/misc/security-transparent-code-level-1.md) . [Kód transparentní pro zabezpečení, sestavení úrovně 2](../../../docs/framework/misc/security-transparent-code-level-2.md) v .NET Framework 4 nebo novějších není ovlivněn silnými názvy. Další informace o změnách v systému zabezpečení najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
 Aplikacím, které přijímají méně než úplný vztah důvěryhodnosti od svého hostitele nebo izolovaného prostoru (sandbox), není povoleno volat sdílené spravované knihovny, pokud modul pro zápis knihovny <xref:System.Security.AllowPartiallyTrustedCallersAttribute> je výslovně nepovoluje prostřednictvím použití atributu. Proto musí autoři aplikací vědět, že některé knihovny nebudou pro ně z částečně důvěryhodného kontextu k dispozici. Ve výchozím nastavení je částečně důvěryhodný všechen kód, který se spouští v [izolovaném prostoru (sandbox)](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) s částečným vztahem důvěryhodnosti a není v seznamu sestavení s úplným vztahem důvěryhodnosti. Neočekáváte-li, že se váš kód má spustit z částečně důvěryhodného kontextu nebo bude volán částečně důvěryhodným kódem, nemusíte mít obavy z informací v této části. Nicméně pokud píšete kód, který musí komunikovat s částečně důvěryhodným kódem nebo pracovat z částečně důvěryhodného kontextu, měli byste vzít v úvahu následující faktory:  
  
- Knihovny musí být podepsány se silným názvem, aby je bylo možné sdílet s více aplikacemi. Silné názvy umožňují <xref:System.AppDomain>, aby váš kód byl umístěn do globální mezipaměti sestavení (GAC) nebo přidaný do seznamu plně důvěryhodných izolovaného prostoru (sandboxing) a umožnil uživatelům ověření, že z vás skutečně pochází konkrétní mobilní kód.  
  
- Ve výchozím nastavení provádí sdílené knihovny se silným názvem [1](../../../docs/framework/misc/security-transparent-code-level-1.md) , které mají pro úplný vztah důvěryhodnosti automaticky implicitní [LinkDemand](../../../docs/framework/misc/link-demands.md) , a to bez toho, aby zapisovač knihovny musel dělat cokoli.  
  
- Pokud volající nemá úplný vztah důvěryhodnosti, ale přesto se pokusí zavolat takovou knihovnu, modul runtime vyvolá výjimku <xref:System.Security.SecurityException> a volající není povolen odkaz na knihovnu.  
  
- Chcete-li zakázat automatický **LinkDemand** a zabránit vyvolání výjimky, můžete umístit atribut **AllowPartiallyTrustedCallersAttribute** do oboru sestavení sdílené knihovny. Tento atribut umožňuje volání knihoven z částečně důvěryhodného spravovaného kódu.  
  
- Částečně důvěryhodný kód, kterému je udělen přístup ke knihovně s tímto atributem, je nadále předmětem dalších omezení definovaných v <xref:System.AppDomain>.  
  
- Neexistuje žádný programový způsob pro částečně důvěryhodný kód pro volání knihovny, která nemá atribut **AllowPartiallyTrustedCallersAttribute** .  
  
 Knihovny, které jsou soukromé pro určitou aplikaci, nevyžadují silný název nebo atribut **AllowPartiallyTrustedCallersAttribute** a nemohou být odkazovány potenciálně škodlivým kódem mimo aplikaci. Takový kód je chráněn proti úmyslnému nebo neúmyslnému zneužití částečně důvěryhodným mobilním kódem, aniž by vývojář musel dělat něco dalšího.  
  
 Měli byste zvážit explicitní povolení použití částečně důvěryhodným kódem pro následující typy kódu:  
  
- Kód, který byl usilovně testován na chyby zabezpečení a je v souladu s pokyny popsanými v pokynech pro [bezpečné kódování](../../standard/security/secure-coding-guidelines.md).  
  
- Knihovny kódu se silným názvem, které jsou speciálně určeny pro částečně důvěryhodné scénáře.  
  
- Všechny součásti (bez ohledu na to, zda jsou částečně nebo plně důvěryhodné) podepsané silným názvem, který bude volán kódem staženým z Internetu.  
  
> [!NOTE]
> Některé třídy v knihovně tříd .NET Framework nemají atribut **AllowPartiallyTrustedCallersAttribute** a nemohou být volány částečně důvěryhodným kódem.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)
