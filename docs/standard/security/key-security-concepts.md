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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400657"
---
# <a name="key-security-concepts"></a>Klíčové koncepty zabezpečení
Rozhraní Microsoft .NET Framework nabízí zabezpečení založené na rolích, které pomáhá řešit problémy se zabezpečením mobilního kódu a poskytuje podporu, která umožňuje součástem určit, k čemu jsou uživatelé oprávněni.  
  
## <a name="type-safety-and-security"></a>Bezpečnost a zabezpečení typů  
 Kód bezpečný pro daný typ přistupuje pouze k umístěním v paměti, ke kterým má oprávnění. (Pro tuto diskusi, typ bezpečnosti konkrétně odkazuje na bezpečnost typu paměti a neměly by být zaměňovány s bezpečnosttypů v širším ohledu.) Kód bezpečný pro daný typ například nemůže číst hodnoty z privátních polí jiného objektu. Přistupuje k typům pouze dobře definovanými a povolenými způsoby.  
  
 Během kompilace just-in-time (JIT) volitelný ověřovací proces zkoumá metadata a Microsoft zprostředkující jazyk (MSIL) metody, která má být zkompilována do nativního strojového kódu k ověření, že jsou typově bezpečné. Tento proces je přeskočen, pokud má kód oprávnění k obejití ověření. Další informace o ověření naleznete v tématu [Managed Execution Process](../../../docs/standard/managed-execution-process.md).  
  
 Přestože ověřování bezpečnosti typů není pro spuštění spravovaného kódu povinné, bezpečnost typů hraje klíčovou roli při izolaci sestavení a vynucení zabezpečení. Pokud je kód typově bezpečný, běžný jazyk runtime může zcela izolovat sestavení od sebe navzájem. Tato izolace pomáhá zajistit, že sestavení nemůže nepříznivě ovlivnit navzájem a zvyšuje spolehlivost aplikace. Součásti bezpečné pro daný typ lze bezpečně spustit ve stejném procesu i v případě, že jsou důvěryhodné na různých úrovních. Pokud kód není typ bezpečný, mohou nastat nežádoucí vedlejší účinky. Například runtime nemůže zabránit spravovanému kódu v volání do nativního (nespravovaného) kódu a provádění škodlivých operací. Pokud je kód typově bezpečný, mechanismus vynucení zabezpečení za běhu zajišťuje, že nemá přístup k nativnímu kódu, pokud k tomu nemá oprávnění. Veškerý kód, který není typ <xref:System.Security.Permissions.SecurityPermission> bezpečný, musí být <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> udělen s předaným členem výčtu ke spuštění.  
  
 Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Objekt zabezpečení  
 Objekt zabezpečení představuje identitu a roli uživatele a jedná jménem uživatele. Zabezpečení založené na rolích v rozhraní .NET Framework podporuje tři druhy objektů zabezpečení:  
  
- Obecné objekty představují uživatele a role, které existují nezávisle na uživatelích a rolích systému Windows.  
  
- Objekty systému Windows představují uživatele systému Windows a jejich role (nebo jejich skupiny systému Windows). Objekt zabezpečení systému Windows může zosobnit jiného uživatele, což znamená, že objekt zabezpečení může přistupovat k prostředku jménem uživatele při prezentaci identity, která patří tomuto uživateli.  
  
- Vlastní objekty mohou být definovány aplikací jakýmkoli způsobem, který je potřeba pro tuto konkrétní aplikaci. Mohou rozšířit základní pojem identity a rolí hlavního povinného.  
  
 Další informace naleznete [v tématu Objekty hlavní a identity](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Authentication  
 Ověřování je proces zjišťování a ověřování identity objektu zabezpečení kontrolou pověření uživatele a ověření těchto pověření proti některé autority. Informace získané během ověřování jsou přímo použitelné vaším kódem. Můžete také použít zabezpečení založené na rolích rozhraní .NET Framework k ověření aktuálního uživatele a k určení, zda chcete povolit tomuto objektu zabezpečení přístup k kódu. Viz přetížení <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> metody příklady, jak ověřit hlavní objekt pro konkrétní role. <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> Přetížení můžete například použít k určení, zda je aktuální uživatel členem skupiny Administrators.  
  
 Dnes se používají různé mechanismy ověřování, z nichž mnohé lze použít se zabezpečením založeným na rolích rozhraní .NET Framework. Některé z nejčastěji používaných mechanismů jsou základní, digest, Passport, operační systém (například NTLM nebo Kerberos) nebo mechanismy definované aplikací.  
  
### <a name="example"></a>Příklad  
 Následující příklad vyžaduje, aby aktivní objekt zabezpečení být správce. Parametr `name` je `null`, který umožňuje každému uživateli, který je správcem předat poptávku.  
  
> [!NOTE]
> V systému Windows Vista určuje nástroj Řízení uživatelských účtů (UAC) oprávnění uživatele. Pokud jste členem předdefinované skupiny Administrators, máte přiřazeny dva přístupové tokeny run-time: token přístupu uživatele se standardním oprávněním a token přístupu správce. Ve výchozím nastavení máte roli standardního uživatele. Chcete-li spustit kód, který vyžaduje, abyste byli správcem, musíte nejprve zvýšit oprávnění ze standardního uživatele na správce. To lze provést při spuštění aplikace klepnutím pravým tlačítkem myši na ikonu aplikace a označením, že chcete spustit jako správce.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 Následující příklad ukazuje, jak určit identitu hlavního povinného a role, které jsou k dispozici pro objekt zabezpečení. Aplikace tohoto příkladu může být potvrzení, že aktuální uživatel je v roli, kterou povolit pro použití aplikace.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autorizace  
 Autorizace je proces určení, zda je objekt zabezpečení povoleno provést požadovanou akci. Autorizace nastane po ověření a používá informace o identitě a rolích objektu zabezpečení k určení, k jakým prostředkům má objekt zabezpečení přístup. K implementaci autorizace můžete použít zabezpečení založené na rolích rozhraní .NET Framework.
