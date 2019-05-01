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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c483baeca9efcbc4a38020a7b2f4fa221a6b4028
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018616"
---
# <a name="key-security-concepts"></a>Klíčové koncepty zabezpečení
Rozhraní Microsoft .NET Framework nabízí na základě rolí zabezpečení umožňující adresu obavy ohledně zabezpečení kvůli mobilní kód a k poskytování podpory, který umožňuje součásti určí, co uživatelé jsou oprávněni provést.  
  
## <a name="type-safety-and-security"></a>Bezpečnost typů a zabezpečení  
 Kód zajišťující bezpečnost typů přistupuje pouze k umístěním paměti, který má oprávnění k přístupu. (V tomto výkladu bezpečnost typů specificky odkazuje na bezpečnost typů paměti a by neměl být zaměňován s bezpečností typů z širšího hlediska.) Například kód zajišťující bezpečnost typů nemůže číst hodnoty z jiného objektu privátní pole. To přistupuje k typům pouze dobře definovanými, přípustnými způsoby.  
  
 Během kompilace just-in-time (JIT) volitelný proces ověření zkoumá metadata a jazyk Microsoft intermediate language (MSIL) metody, chcete-li být JIT kompilován do nativního strojového kódu k ověření, že jsou typově bezpečné. Tento proces je vynechán, pokud kód má oprávnění obejít ověření. Další informace o ověřování najdete v tématu [Managed Execution Process](../../../docs/standard/managed-execution-process.md).  
  
 Ačkoli ověření bezpečnosti typů není povinné pro spuštění spravovaného kódu, bezpečnost typů hraje rozhodující roli v izolaci sestavení a prosazování zabezpečení. Pokud je kód typově bezpečný, modul common language runtime může zcela izolovat sestavení od sebe navzájem. Tato izolace pomáhá zajistit, že sestavení nemohou navzájem nepříznivě ovlivňovat a také zvyšuje spolehlivost aplikace. Komponenty zajišťující bezpečnost typů mohou bezpečně běžet ve stejném procesu i v případě, že jsou důvěryhodné na různých úrovních. Když kód není typově bezpečný, může dojít k nežádoucí vedlejší účinky. Například modul runtime nemůže bránit spravovanému kódu z volání do nativního (nespravovaného) kódu a provádění škodlivých operací. Pokud je kód typově bezpečný, mechanismus pro prosazování zabezpečení modulu runtime zajišťuje, že nepřistupuje nativního kódu pouze pokud má oprávnění k tomuto. Veškerý kód, který není typově bezpečný musí být udělena <xref:System.Security.Permissions.SecurityPermission> s předaným členem výčtu <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> ke spuštění.  
  
 Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Objekt zabezpečení  
 Objekt zabezpečení představuje identitu a roli uživatele a funguje jménem uživatele. Zabezpečení na základě rolí v rozhraní .NET Framework podporuje tři typy objektů:  
  
- Obecné objekty představují uživatele a role, které existují nezávisle na Windows uživatelů a rolí.  
  
- Objekty zabezpečení Windows představují uživatelům Windows a jejich role (nebo jejich skupin Windows). Objekt zabezpečení Windows můžou zosobňovat jiného uživatele, což znamená, že objekt zabezpečení získat přístup k prostředku jménem uživatele, zatímco uvádí identitu, která patří do tohoto uživatele.  
  
- Lze definovat vlastní objekty zabezpečení aplikací žádným způsobem, který je potřebný pro tuto aplikaci. Mohou rozšířit základní pojem daného objektu zabezpečení identity a rolí.  
  
 Další informace najdete v tématu [instanční objekt a objekty Identity](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Ověřování  
 Ověřování je proces zjišťování a ověření identity objektu zabezpečení ve zkoumání přihlašovacích údajů uživatele a ověření těchto přihlašovacích údajů, kteří některé autoritu. Informace získané při ověřování je možné přímo použít kód. Zabezpečení na základě rolí rozhraní .NET Framework můžete použít také k ověření aktuálního uživatele a na zjištění, jestli se má povolit tohoto instančního objektu pro přístup ke kódu. V tématu přetížení <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> metoda příklady toho, jak ověřování objektu pro konkrétní role. Například můžete použít <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> přetížení k určení, zda je aktuální uživatel členem skupiny Administrators.  
  
 Širokou škálu ověřovací mechanismy, které se dnes používají, z nichž lze použít s zabezpečení na základě rolí rozhraní .NET Framework. Některé z nejčastěji používaných mechanismy jsou basic, digest, Passport, operačního systému (například Kerberos nebo NTLM) nebo mechanismy definované aplikací.  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu vyžaduje aktivní objekt zabezpečení správce. `name` Parametr `null`, což umožňuje každému uživateli, který je správcem, předat požadavek.  
  
> [!NOTE]
>  Řízení uživatelských účtů (UAC) v systému Windows Vista, určuje oprávnění uživatele. Pokud jste členem předdefinované skupiny Administrators, máte přiřazeny dva přístupové tokeny run-time: token přístupu uživatele se standardním oprávněním a token přístupu správce. Ve výchozím nastavení máte roli standardního uživatele. Pokud chcete spustit kód, který je potřeba mít oprávnění správce, musíte nejprve zvýšit své oprávnění ze standardního uživatele na správce. To můžete provést při spuštění aplikace tak, že kliknete pravým tlačítkem na ikonu aplikace a označující, že chcete spustit jako správce.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 Následující příklad ukazuje, jak k určení identity objektu zabezpečení a rolí, které jsou k dispozici pro objekt zabezpečení. Aplikace v tomto příkladu může být potvrďte, že je aktuální uživatel v roli, kterou můžete povolit pro vaši aplikaci používají.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autorizace  
 Autorizace je procesu, který určuje, jestli objekt může provést požadovanou akci. Autorizace dochází po ověřování a používá informace o identitě daného objektu zabezpečení a rolích k určení, jaké prostředky přístup k objektu zabezpečení. Zabezpečení na základě rolí rozhraní .NET Framework můžete použít k implementaci autorizace.
