---
title: "Objekty zabezpečení a identity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02c8b4b9f46f051e42fb2ae85a39b6ff48ad2f1a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="principal-and-identity-objects"></a>Objekty zabezpečení a identity
Spravovaný kód můžete zjistit identitu nebo roli objektu zabezpečení prostřednictvím <xref:System.Security.Principal.IPrincipal> objekt, který obsahuje odkaz na <xref:System.Security.Principal.IIdentity> objektu. Může to být užitečné k porovnání objektů identity a zabezpečení do známých pojmů jako účty uživatelů a skupin. Ve většině prostředí sítě představují uživatelské účty uživatele nebo programy, zatímco skupinové účty představují určité kategorie uživatelů a práv, které mohou mít. Objekty identity rozhraní .NET Framework podobně představují uživatele, zatímco role představují členství a kontexty zabezpečení. Objekt zabezpečení v rozhraní .NET Framework zapouzdří objekt identity a rolí. Aplikace rozhraní .NET framework udělit práva k objektu zabezpečení na základě svou identitu nebo běžně, členství v roli.  
  
## <a name="identity-objects"></a>Objekty identity  
 Objekt identity zapouzdřuje informace o uživateli nebo ověřovaná entita. Objekty identity na své nejzákladnější úrovni obsahovat název a typ ověření. Název může být buď uživatelské jméno nebo název účtu systému Windows, když typ ověřování, který může být buď protokol podporovaného přihlášení, jako je například protokol Kerberos V5, nebo vlastní hodnota. Definuje rozhraní .NET Framework <xref:System.Security.Principal.GenericIdentity> objekt, který lze použít pro většinu vlastních scénářů přihlašování a více specializované <xref:System.Security.Principal.WindowsIdentity> objekt, který lze použít, pokud má vaše aplikace využívají ověřování systému Windows. Kromě toho můžete definovat svou vlastní třídu identity, který zapouzdřuje vlastní uživatelské informace.  
  
 <xref:System.Security.Principal.IIdentity> Rozhraní definuje vlastnosti pro přístup k názvu a typu ověřování, jako je například Kerberos verze 5 nebo protokolu NTLM. Všechny **Identity** implementace třídy **identita** rozhraní. Není nutná relace mezi **Identity** objektu a proces systému Windows NT token v rámci které vlákno právě probíhá. Ale pokud **Identity** objekt **WindowsIdentity** objektu, se předpokládá, že identita představuje token zabezpečení systému Windows NT.  
  
## <a name="principal-objects"></a>Hlavní objekty  
 Objekt zabezpečení představuje kontext zabezpečení, v němž je spuštěn kód. Aplikace, které implementují zabezpečení na základě rolí udělit práva na základě role přidružené k objektu zabezpečení. Podobně jako objekty identity, poskytuje rozhraní .NET Framework <xref:System.Security.Principal.GenericPrincipal> objektu a <xref:System.Security.Principal.WindowsPrincipal> objektu. Můžete také definovat vlastní hlavní třídy.  
  
 <xref:System.Security.Principal.IPrincipal> Rozhraní definuje vlastnosti pro přístup přiřazený **Identity** objektu i metodu pro určení, zda uživatel identifikovaný **hlavní** objektu je členem skupiny dané role. Všechny **hlavní** implementace třídy **IPrincipal** rozhraní také všechny další vlastnosti a metody, které jsou nezbytné. Například poskytuje modul common language runtime **WindowsPrincipal** třídy, která implementuje další funkce pro mapování členství ve skupině Windows NT nebo Windows 2000 k rolím.  
  
 A **hlavní** objekt je vázán na kontext volání (<xref:System.Runtime.Remoting.Messaging.CallContext>) objekt v rámci domény aplikace (<xref:System.AppDomain>). Výchozí kontext volání je vytvořen vždy s jednotlivými nové **AppDomain**, takže je vždy k dispozici pro příjem volání kontextu **hlavní** objektu. Při vytváření nové vlákno **CallContext** pro vlákno je taky vytvořit objekt. **Hlavní** odkaz automaticky zkopírován z vytvářeného vlákna na nové vlákno **CallContext**. Pokud modul runtime nemůže určit, který **hlavní** patří tvůrci vlákna, následuje výchozí zásady pro **hlavní** a **Identity** objektu vytvoření.  
  
 Zásady specifické pro doménu aplikace konfigurovat definuje pravidla pro při rozhodování o tom, jaký druh **hlavní** objekt, který chcete přidružit k nové doméně aplikace. Pokud to umožňují zásady zabezpečení, může vytvořit modul runtime **hlavní** a **Identity** objekty, které odráží token operačního systému přidružené k aktuální vlákno provádění. Ve výchozím nastavení, modul runtime používá **hlavní** a **Identity** objekty, které představují neověřené uživatele. Modul runtime nevytváří tyto výchozí **hlavní** a **Identity** objekty, dokud se kód se pokusí přistupovat k nim.  
  
 Důvěryhodný kód, který vytváří doménu aplikace můžete nastavit zásady domény aplikace, která řídí konstrukci výchozí **hlavní** a **Identity** objekty. Tyto zásady specifické pro doménu aplikace platí pro všechny spuštěné vlákna v této doméně. Nespravovaný, důvěryhodný hostitel ze své podstaty má možnost nastavit tyto zásady, ale musí mít spravovaného kódu, který nastaví tuto zásadu <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> pro ovládání zásad domény.  
  
 Při přenosu **hlavní** objektů mezi doménami aplikací, ale v rámci stejného procesu (a proto na stejném počítači), vzdálená infrastruktura zkopíruje odkaz na **hlavní** objekt spojený s kontextem volajícího volaný kontext.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření objektu WindowsPrincipal](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)  
 [Postupy: Vytváření objektů GenericPrincipal a GenericIdentity](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)  
 [Nahrazení objektu zabezpečení](../../../docs/standard/security/replacing-a-principal-object.md)  
 [Zosobnění a návrat](../../../docs/standard/security/impersonating-and-reverting.md)  
 [Zabezpečení na základě rolí](../../../docs/standard/security/role-based-security.md)  
 [Klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md)
