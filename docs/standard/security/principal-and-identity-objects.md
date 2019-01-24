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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c5b74f2608022d48dbd7e63e4ddf6112c333e3f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604398"
---
# <a name="principal-and-identity-objects"></a>Objekty zabezpečení a identity
Spravovaný kód může zjišťovat identitu nebo role objekt zabezpečení prostřednictvím <xref:System.Security.Principal.IPrincipal> objektu, který obsahuje odkaz na <xref:System.Security.Principal.IIdentity> objektu. Může být užitečné k porovnání objektů identity a zabezpečení na známé koncepty, jako jsou účty uživatelů a skupin. Ve většině prostředí sítě představují uživatelské účty uživatele nebo programy, zatímco skupinových účtů představují určité kategorie uživatelů a práv, které mohou mít. Obdobně objekty rozhraní .NET Framework identity představují uživatele, zatímco role představují členství ve skupinách a kontext zabezpečení. V rozhraní .NET Framework zapouzdří objekt zabezpečení identity objektu a rolí. Aplikace rozhraní .NET framework udělit práva k objektu zabezpečení na základě své identity nebo častěji, členství v roli.  
  
## <a name="identity-objects"></a>Objekty identity  
 Identita objektu zapouzdřuje informace o uživateli nebo ověřovaná entita. Na nejzákladnější úrovni identity objekty obsahují název a typ ověřování. Název může být buď uživatelské jméno nebo název účtu Windows, typ ověřování mohou být protokol podporovaný přihlášení, třeba Kerberos v. 5, nebo vlastní hodnotu. Definuje rozhraní .NET Framework <xref:System.Security.Principal.GenericIdentity> objekt, který lze použít pro většinu scénářů vlastní přihlášení a další specializované <xref:System.Security.Principal.WindowsIdentity> objekt, který můžete použít, pokud chcete, aby vaše aplikace přináší setrvávání u ověřování Windows. Kromě toho můžete definovat vlastní identity třídu, která zapouzdřuje vlastní uživatelské informace.  
  
 <xref:System.Security.Principal.IIdentity> Rozhraní definuje vlastnosti pro přístup k názvu a typu ověřování, jako je například V5 protokolu Kerberos nebo NTLM. Všechny **Identity** implementace třídy **IIdentity** rozhraní. Není nutná relace mezi **Identity** objektu a proces Windows NT token v rámci které vlákno právě probíhá. Ale pokud **Identity** je objekt **WindowsIdentity** objektu, předpokládá se identita představuje token zabezpečení systému Windows NT.  
  
## <a name="principal-objects"></a>Hlavní objekty  
 Objekt zabezpečení představuje kontextu zabezpečení, pod kterým běží kód. Aplikace, které implementují zabezpečení na základě rolí udělit práva na základě role přidružené k objektu zabezpečení. Podobně jako objekty identity, poskytuje rozhraní .NET Framework <xref:System.Security.Principal.GenericPrincipal> objektu a <xref:System.Security.Principal.WindowsPrincipal> objektu. Můžete také definovat své vlastní základní třídy.  
  
 <xref:System.Security.Principal.IPrincipal> Rozhraní definuje vlastnosti pro přístup přiřazený **Identity** objektu a také metodu pro určení, zda uživatel identifikován **hlavní** objektu je členem skupiny podle role. Všechny **hlavní** implementace třídy **IPrincipal** rozhraní stejně jako další vlastnosti a metody, které jsou nezbytné. Například poskytuje modul common language runtime **WindowsPrincipal** třídy, která implementuje další funkce pro mapování členství ve skupině Windows NT nebo Windows 2000 k rolím.  
  
 A **hlavní** je objekt vázán na kontext volání (<xref:System.Runtime.Remoting.Messaging.CallContext>) objekt v rámci domény aplikace (<xref:System.AppDomain>). Výchozí kontext volání je vždy byla vytvořena s každým nová **AppDomain**, takže je vždy k dispozici pro příjem kontext volání **hlavní** objektu. Při vytvoření nového vlákna **CallContext** pro vlákno je taky vytvořit objekt. **Hlavní** odkaz na objekt je automaticky zkopírují z vytvářeného vlákna do nového vlákna **CallContext**. Pokud modul runtime nelze určit, která **hlavní** patří autorovi vlákna, následuje výchozí zásady pro **hlavní** a **Identity** objektu vytvoření.  
  
 Konfigurovatelné specifického pro doménu zásady aplikace definuje pravidla pro rozhodování o tom, jaký typ **hlavní** objektu, který chcete přidružit k nové doméně aplikace. Pokud to umožňují zásady zabezpečení, můžete vytvořit modul runtime **hlavní** a **Identity** objekty, které zahrnují token operačního systému přidružený k aktuální vlákno provádění. Ve výchozím nastavení, modul runtime používá **hlavní** a **Identity** objekty, které představují neověřené uživatele. Modul runtime nevytvoří tyto výchozí **hlavní** a **Identity** objekty, dokud se kód se pokusí přistupovat k nim.  
  
 Důvěryhodný kód, který vytvoří aplikační doménu můžete nastavit zásady domény aplikace, která řídí vytváření výchozích **hlavní** a **Identity** objekty. Tato zásada specifického pro doménu aplikace se vztahuje na všechna vlákna provádění v této doméně aplikace. Nespravované, důvěryhodný hostitel má ze své podstaty schopnost nastavovat tyto zásady, ale musí být spravovaný kód, který nastaví tyto zásady <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> pro řízení zásad domény.  
  
 Při přenosu **hlavní** objektů mezi doménami aplikace, ale v rámci stejného procesu (a proto na stejném počítači), infrastrukturou vzdálené komunikace zkopíruje odkaz na **hlavní** objekt přidružený k volajícího kontextu volaného kontext.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření objektu WindowsPrincipal](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)
- [Postupy: Vytváření objektů GenericPrincipal a GenericIdentity – objekty](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)
- [Nahrazení objektu zabezpečení](../../../docs/standard/security/replacing-a-principal-object.md)
- [Zosobnění a návrat](../../../docs/standard/security/impersonating-and-reverting.md)
- [Zabezpečení na základě rolí](../../../docs/standard/security/role-based-security.md)
- [Klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md)
