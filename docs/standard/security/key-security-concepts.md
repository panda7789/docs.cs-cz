---
title: "Klíčové koncepty zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e29b3c12fe89861574741506cb7cd018eb81b1d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="key-security-concepts"></a>Klíčové koncepty zabezpečení
Rozhraní Microsoft .NET Framework nabízí na základě rolí zabezpečení pomohou adresu zabezpečení se o mobilního kódu a poskytovat podporu, která umožňuje součásti, které chcete zjistit, co uživatelé jsou oprávněni provést.  
  
## <a name="type-safety-and-security"></a>Typ zabezpečení a zabezpečení  
 Typově bezpečný kód přistupuje pouze na umístění paměti, která má oprávnění k přístupu. (V tomto výkladu bezpečnost typů konkrétně odkazuje na bezpečnost typů paměti a nesmí být zaměňovat s bezpečnost typů z hlediska širší.) Například kód bezpečnost typů nelze načíst hodnoty z privátním polím jiný objekt. Přistupuje k typům pouze způsoby dobře definovaný, povolená.  
  
 Během kompilace za běhu (JIT) volitelný proces ověření prozkoumá metadat a Microsoft (MSIL intermediate language) metody být kompilována do nativního kódu počítače k ověření, že jsou bezpečného typu. Tento proces se přeskočí, pokud kód oprávnění obejít ověření. Další informace o ověření najdete v tématu [spravovat proces spuštění](../../../docs/standard/managed-execution-process.md).  
  
 I když ověření bezpečnosti typů není povinné pro spuštění spravovaného kódu, bezpečnost typů hraje zásadní roli v sestavení izolace a zabezpečení vynucení. Pokud je kód typově bezpečný, můžete modul common language runtime zcela izolovat sestavení od sebe navzájem. Tato izolace pomáhá zajistit, že sestavení nemůže mít nepříznivý vliv na sebe navzájem a zvyšuje spolehlivost aplikace. Typově bezpečný součásti mohou bezpečně v rámci jednoho procesu i v případě, že jsou na různých úrovních důvěryhodné. Pokud kód není typově bezpečný, může dojít k nežádoucí vedlejší účinky. Například modul runtime nemohou zabránit spravovaného kódu z volání do nativního kódu (nespravovaný) a provádění operací se zlými úmysly. Pokud je kód typově bezpečný, modul runtime zabezpečení implementační mechanismus zaručuje, že ho není připojit nativního kódu pouze pokud má oprávnění k tomu. Všechny kód, který není typu bezpečné musí být udělena <xref:System.Security.Permissions.SecurityPermission> s předaným členem výčtu <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> ke spuštění.  
  
 Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Objekt zabezpečení  
 Objekt zabezpečení představuje identitu a roli uživatele a funguje jménem uživatele. Na základě rolí zabezpečení v rozhraní .NET Framework podporuje tři typy objektů:  
  
-   Obecné objekty zabezpečení představují uživatelů a rolí, které existují nezávisle na Windows uživatelů a rolí.  
  
-   Objekty zabezpečení systému Windows představují uživatele systému Windows a jejich rolí (nebo jejich skupin systému Windows). Objekt zabezpečení systému Windows může zosobňovat jiného uživatele, což znamená, že objekt můžete získat přístup k prostředku na uživatele při uvádí identitu, která patří do tohoto uživatele.  
  
-   Vlastní objekty lze definovat pomocí aplikace žádným způsobem, který je potřebný pro konkrétní aplikaci. Mohou rozšířit základní představu o identity objektu zabezpečení a rolí.  
  
 Další informace najdete v tématu [objekt zabezpečení a identita objekty](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Ověřování  
 Ověřování je proces zjišťování a ověřování identity objektu zabezpečení tak, že prověří pověření uživatele a ověření těchto pověření podle některé autority. Informace získané při ověřování je přímo použitelná pro váš kód. Zabezpečení na základě rolí rozhraní .NET Framework slouží také k ověřování aktuálního uživatele a k určení, zda povolit tomuto objektu zabezpečení přístupu kódu. V tématu přetížení <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> metodu pro příklady, jak ověřit objekt zabezpečení pro konkrétní role. Například můžete použít <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> přetížení k určení, zda je aktuální uživatel členem skupiny Administrators.  
  
 Dnes se používají různé mechanismy ověřování, mnoho z nichž lze použít s zabezpečení na základě rolí rozhraní .NET Framework. Některé z nejčastěji používaných mechanismů jsou základní, ověřování algoritmem digest, Passport, operačního systému (například protokolu NTLM nebo Kerberos) nebo mechanismy definované aplikací.  
  
### <a name="example"></a>Příklad  
 Následující příklad vyžaduje, aby aktivní objekt zabezpečení správce. `name` Parametr `null`, což umožňuje každý uživatel, který je správcem předat požadavek.  
  
> [!NOTE]
>  Řízení uživatelských účtů (UAC) v systému Windows Vista, určuje oprávnění uživatele. Pokud jste členem předdefinované skupiny Administrators, máte přiřazeny dva přístupové tokeny run-time: token přístupu uživatele se standardním oprávněním a token přístupu správce. Ve výchozím nastavení máte roli standardního uživatele. Kód, který vyžaduje, abyste správce provést, musíte nejprve zvýšit vaše oprávnění ze standardního uživatele pro správce. Můžete to provést při spuštění aplikace tak, že kliknete pravým tlačítkem na ikonu aplikace a indikující, že chcete spustit jako správce.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 Následující příklad ukazuje, jak zjistit identitu objektu zabezpečení a rolí, které jsou k dispozici pro objekt zabezpečení. Aplikace v tomto příkladu může být potvrďte, že aktuální uživatel je v roli, kterou můžete povolit pro používání vaší aplikace.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autorizace  
 Autorizace je proces pro určení toho, zda objekt může provést požadovanou akci. Autorizace dochází po ověření a používá informace o objektu zabezpečení identity a rolí k určení, jaké prostředky přístup k objektu zabezpečení. Rozhraní .NET Framework na základě rolí zabezpečení můžete použít k implementaci autorizace.
