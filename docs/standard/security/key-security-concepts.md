---
title: Klíčové koncepty zabezpečení
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
ms.openlocfilehash: b7bcb7e56ca14d129eadcaeac19452d4a443713d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705969"
---
# <a name="key-security-concepts"></a>Klíčové koncepty zabezpečení
Microsoft .NET Framework nabízí zabezpečení na základě rolí, které umožňuje řešit problémy zabezpečení mobilního kódu a poskytovat podporu, která umožňuje komponentám určit, kteří uživatelé mají oprávnění dělat.  
  
## <a name="type-safety-and-security"></a>Bezpečnost typů a zabezpečení  
 Kód zajišťující bezpečnost typů přistupuje pouze k umístěním paměti, ke kterým má oprávnění přistupovat. (Pro tuto diskuzi, bezpečnost typů konkrétně odkazuje na bezpečnost typů paměti a neměla by být zaměňována s bezpečností typů v širším ohledu.) Například kód zajišťující bezpečnost typů nemůže číst hodnoty z privátních polí jiného objektu. Přistupuje pouze k typům v dobře definovaných, přípustných způsobech.  
  
 Během kompilace just-in-time (JIT) ověří volitelný proces ověření metadata a jazyk MSIL (Microsoft Intermediate Language) metody, která má být zkompilována JIT do nativního strojového kódu, aby ověřil, zda jsou typově bezpečná. Tento proces se přeskočí, pokud má kód oprávnění obejít ověřování. Další informace o ověřování najdete v tématu [proces spravovaného spuštění](../../../docs/standard/managed-execution-process.md).  
  
 I když ověření bezpečnosti typu není nutné pro spuštění spravovaného kódu, bezpečnost typů hraje zásadní roli v izolaci sestavení a vynucení zabezpečení. Pokud je kód typově bezpečný, modul CLR (Common Language Runtime) může zcela izolovat sestavení od sebe navzájem. Tato izolace pomáhá zajistit, že sestavení nemůžou negativně ovlivnit a zvyšuje spolehlivost aplikace. Typově bezpečné komponenty se můžou bezpečně spouštět ve stejném procesu, i když jsou důvěryhodné na různých úrovních. Pokud kód není typově bezpečný, může dojít k nežádoucím vedlejším účinkům. Modul runtime například nemůže zabránit spravovanému kódu v volání nativního (nespravovaného) kódu a provádění škodlivých operací. Pokud je kód typově bezpečný, mechanismus vynucování zabezpečení modulu runtime zajišťuje, aby nezískal přístup k nativnímu kódu, pokud k tomu nemá oprávnění. Veškerý kód, který není typově bezpečný, musí být udělen <xref:System.Security.Permissions.SecurityPermission> s předaným členem výčtu <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> ke spuštění.  
  
 Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Objekt zabezpečení  
 Objekt zabezpečení představuje identitu a roli uživatele a pracuje jménem uživatele. Zabezpečení na základě rolí v .NET Framework podporuje tři druhy objektů zabezpečení:  
  
- Obecné objekty zabezpečení reprezentují uživatele a role, které existují nezávisle na uživatelích a rolích systému Windows.  
  
- Objekty zabezpečení systému Windows reprezentují uživatele systému Windows a jejich role (nebo jejich skupiny systému Windows). Objekt zabezpečení systému Windows může zosobnit jiného uživatele, což znamená, že objekt zabezpečení má přístup k prostředku jménem uživatele, přičemž prezentuje identitu patřící tomuto uživateli.  
  
- Vlastní objekty zabezpečení mohou být definovány aplikací jakýmkoli způsobem, který je potřeba pro konkrétní aplikaci. Můžou zvětšit základní pojem identity a rolí objektu zabezpečení.  
  
 Další informace najdete v tématu [objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Ověřování  
 Ověřování je proces zjišťování a ověřování identity objektu zabezpečení prozkoumáním přihlašovacích údajů uživatele a ověřením těchto přihlašovacích údajů proti nějaké autoritě. Informace získané během ověřování jsou přímo použitelné vaším kódem. Můžete také použít .NET Framework zabezpečení založené na rolích k ověření aktuálního uživatele a určení, zda chcete, aby tento objekt zabezpečení měl přístup k vašemu kódu. Příklady ověřování objektu zabezpečení pro konkrétní role naleznete v tématu přetížení metody <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType>. Například můžete použít přetížení <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> k určení, zda je aktuální uživatel členem skupiny Administrators.  
  
 Dnes se používá celá řada ověřovacích mechanismů, mnohé z nich je možné použít s .NET Framework zabezpečení na základě rolí. Některé z nejčastěji používaných mechanismů jsou Basic, Digest, Passport, operační systém (například NTLM nebo Kerberos) nebo mechanizmy definované aplikací.  
  
### <a name="example"></a>Příklad  
 Následující příklad vyžaduje, aby aktivní objekt zabezpečení byl správce. Parametr `name` je `null`, který umožňuje každému uživateli, který je správcem, předat požadavek.  
  
> [!NOTE]
> V systému Windows Vista Určuje nástroj řízení uživatelských účtů oprávnění uživatele. Pokud jste členem předdefinované skupiny Administrators, máte přiřazeny dva přístupové tokeny run-time: token přístupu uživatele se standardním oprávněním a token přístupu správce. Ve výchozím nastavení máte roli standardního uživatele. Chcete-li spustit kód, který vyžaduje, abyste byli správcem, musíte nejprve zvýšit oprávnění ze standardního uživatele na správce. To můžete provést po spuštění aplikace kliknutím pravým tlačítkem myši na ikonu aplikace a označením, že chcete spustit jako správce.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 Následující příklad ukazuje, jak určit identitu objektu zabezpečení a role, které jsou k dispozici pro objekt zabezpečení. Účelem tohoto příkladu je ověřit, zda je aktuální uživatel v roli, kterou povolíte pro použití vaší aplikace.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autorizace  
 Autorizace je proces určení, zda může objekt zabezpečení provést požadovanou akci. K ověření dochází po ověření a používá informace o identitě a rolích objektu zabezpečení k určení prostředků, ke kterým má objekt zabezpečení přístup. K implementaci autorizace můžete použít .NET Framework zabezpečení na základě rolí.
