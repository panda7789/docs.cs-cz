---
title: Objekty zabezpečení a identity
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET Framework], identity objects
- principal objects, about principal objects
- security [.NET Framework], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
ms.openlocfilehash: c2fadc2d5bb3a787123678a93fa96f8966debbd5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705948"
---
# <a name="principal-and-identity-objects"></a>Objekty zabezpečení a identity
Spravovaný kód může zjistit identitu nebo roli objektu zabezpečení prostřednictvím objektu <xref:System.Security.Principal.IPrincipal>, který obsahuje odkaz na objekt <xref:System.Security.Principal.IIdentity>. Může být užitečné porovnat identity a objekty zabezpečení s známými koncepty, jako jsou účty uživatelů a skupin. Ve většině síťových prostředí představují uživatelské účty osoby nebo programy, zatímco účty skupin představují určité kategorie uživatelů a práva, která mají. Podobně .NET Framework objekty identity představuje uživatele, zatímco role reprezentují členství a kontexty zabezpečení. V .NET Framework objekt zabezpečení zapouzdřuje objekt identity i roli. .NET Framework aplikace udělují oprávnění objektu zabezpečení na základě jeho identity nebo častěji jeho členství v rolích.  
  
## <a name="identity-objects"></a>Objekty identity  
 Objekt identity zapouzdřuje informace o ověřovaném uživateli nebo entitě. Na nejzákladnější úrovni objekty identity obsahují název a typ ověřování. Název může být buď jméno uživatele, nebo název účtu systému Windows, zatímco typ ověřování může být buď podporovaný přihlašovací protokol, jako je například Kerberos V5, nebo vlastní hodnota. .NET Framework definuje objekt <xref:System.Security.Principal.GenericIdentity>, který se dá použít pro většinu vlastních scénářů přihlášení a konkrétnější objekt <xref:System.Security.Principal.WindowsIdentity>, který se dá použít, když chcete, aby se vaše aplikace spoléhala na ověřování systému Windows. Kromě toho můžete definovat vlastní třídu identity, která zapouzdřuje vlastní informace o uživateli.  
  
 Rozhraní <xref:System.Security.Principal.IIdentity> definuje vlastnosti pro přístup k názvu a typu ověřování, jako je například Kerberos V5 nebo NTLM. Všechny třídy **identity** implementují rozhraní **IIdentity** . Mezi objektem **identity** a tokenem procesu Windows NT, na kterém je vlákno aktuálně prováděno, není vyžadována žádná relace. Pokud je však objekt **identity** objekt **WindowsIdentity** , předpokládá se, že identita představuje token zabezpečení systému Windows NT.  
  
## <a name="principal-objects"></a>Objekty zabezpečení  
 Objekt zabezpečení představuje kontext zabezpečení, pod kterým je spuštěn kód. Aplikace, které implementují zabezpečení na základě rolí, poskytují práva na základě role přidružené k objektu zabezpečení. Podobně jako u objektů identity .NET Framework poskytuje objekt <xref:System.Security.Principal.GenericPrincipal> a objekt <xref:System.Security.Principal.WindowsPrincipal>. Můžete také definovat vlastní třídy zabezpečení.  
  
 Rozhraní <xref:System.Security.Principal.IPrincipal> definuje vlastnost pro přístup k objektu přidružené **identity** a také ke způsobu určení, zda je uživatel identifikovaný objektem **zabezpečení** členem dané role. Všechny třídy **zabezpečení** implementují rozhraní **IPrincipal** a také všechny další vlastnosti a metody, které jsou nezbytné. Například modul CLR (Common Language Runtime) poskytuje třídu **WindowsPrincipal** , která implementuje další funkce pro mapování členství ve skupině Windows NT nebo Windows 2000 na role.  
  
 Objekt **zabezpečení** je svázán s objektem kontextu volání (<xref:System.Runtime.Remoting.Messaging.CallContext>) v doméně aplikace (<xref:System.AppDomain>). Výchozí kontext volání je vždy vytvořen s každou novou **doménou AppDomain**, takže je k dispozici vždy kontext volání pro přijetí objektu **zabezpečení** . Při vytvoření nového vlákna je také vytvořen objekt **CallContext** pro vlákno. Odkaz na objekt **zabezpečení** je automaticky zkopírován z vytvářeného vlákna do **CallContext**nového vlákna. Pokud modul runtime nemůže určit, který objekt **zabezpečení** patří tvůrci vlákna, následuje za výchozí zásadou pro vytvoření objektu **zabezpečení** a **identity** .  
  
 Konfigurovatelné zásady specifické pro doménu aplikace definují pravidla pro rozhodování o tom, jaký typ objektu **zabezpečení** má být přidružen k nové doméně aplikace. V případě povolení zásad zabezpečení může modul runtime vytvořit objekty **zabezpečení** a **identity** , které odráží token operačního systému přidružený k aktuálnímu vláknu provádění. Ve výchozím nastavení používá modul runtime objekty **Principal** a **identity** , které reprezentují neověření uživatelé. Modul runtime nevytváří tyto výchozí objekty **zabezpečení** a **identity** , dokud se kód nepokusí o přístup k nim.  
  
 Důvěryhodný kód, který vytváří doménu aplikace, může nastavit zásady domény aplikace, které řídí konstrukci výchozích objektů **zabezpečení** a objektů **identity** . Tato zásada specifická pro doménu aplikace platí pro všechna prováděcí vlákna v dané doméně aplikace. Nespravovaný, důvěryhodný hostitel má v podstatě možnost nastavit tuto zásadu, ale spravovaný kód, který tuto zásadu nastavuje, musí mít <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> pro řízení zásad domény.  
  
 Při přenosu objektu **zabezpečení** mezi doménami aplikace, ale v rámci stejného procesu (a proto ve stejném počítači), infrastruktura vzdálené komunikace zkopíruje odkaz na objekt **zabezpečení** přidružený k kontextu volajícího do kontextu volaného.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření objektu WindowsPrincipal](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)
- [Postupy: Vytváření objektů GenericPrincipal a GenericIdentity](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)
- [Nahrazení objektu zabezpečení](../../../docs/standard/security/replacing-a-principal-object.md)
- [Zosobnění a návrat](../../../docs/standard/security/impersonating-and-reverting.md)
- [Zabezpečení na základě rolí](../../../docs/standard/security/role-based-security.md)
- [Klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md)
