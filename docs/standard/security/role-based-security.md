---
title: Zabezpečení na základě rolí
ms.date: 07/15/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET]
- security [.NET], role-based
- permissions [.NET], principals
- authentication [.NET], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
ms.openlocfilehash: ed6c33be5a5da066e238c160da8bff8d25cb68fc
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555669"
---
# <a name="role-based-security"></a>Zabezpečení na základě rolí

Role se často používají ve finančních nebo obchodních aplikacích k vymáhání zásad. Například aplikace může stanovit omezení velikosti zpracovávané transakce v závislosti na tom, zda uživatel, který požadavek odeslal, je členem zadané role. Přípravci můžou mít autorizaci pro zpracování transakcí, které jsou menší než zadané prahové hodnoty, můžou mít vedoucí vyšší limit a místopředsedé můžou mít pořád vyšší limit (nebo vůbec neplatí žádné omezení). Zabezpečení na základě rolí lze použít také v případě, že aplikace vyžaduje více schválení pro dokončení akce. Takový případ může být nákupní systém, ve kterém může kterýkoli zaměstnanec vygenerovat žádost o nákup, ale jenom pro nákupního agenta může tuto žádost převést na nákupní objednávku, kterou je možné odeslat dodavateli.  
  
 Zabezpečení založené na rolích .NET podporuje autorizaci tím, že vytváří informace o objektu zabezpečení, který je vytvořen z přidružené identity, k dispozici pro aktuální vlákno. Identitu (a objekt zabezpečení, který pomáhá definovat), může být buď založen na účtu systému Windows, nebo se jednat o vlastní identitu, která se nevztahuje k účtu systému Windows. Aplikace .NET mohou provádět rozhodnutí o autorizaci na základě identity nebo členství v roli objektu zabezpečení nebo obojího. Role je pojmenovaná sada objektů zabezpečení, které mají stejná oprávnění s ohledem na zabezpečení (například správce oznámení nebo správce). Objekt zabezpečení může být členem jedné nebo více rolí. Proto mohou aplikace použít členství v rolích k určení, zda je objekt zabezpečení autorizován k provedení požadované akce.  
  
 Pro zajištění snadného použití a konzistence se zabezpečením přístupu kódu poskytuje zabezpečení založené na rolích .NET <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> objekty, které umožňují společnému jazykovým modulům runtime provádět autorizaci způsobem, který je podobný kontrole zabezpečení přístupu kódu. <xref:System.Security.Permissions.PrincipalPermission>Třída představuje identitu nebo roli, které musí objekt zabezpečení souhlasit a je kompatibilní s deklarativními a imperativními kontrolami zabezpečení. K informacím o identitě objektu zabezpečení můžete také přistupovat přímo a v případě potřeby provádět kontroly rolí a identit v kódu.  
  
 Rozhraní .NET poskytuje podporu zabezpečení na základě rolí, která je flexibilní a rozšiřitelná tak, aby vyhovovala potřebám spektra aplikací. Můžete se rozhodnout, že budete spolupracovat se stávajícími ověřovacími infrastrukturami, jako jsou služby COM+ 1,0, nebo vytvořit vlastní ověřovací systém. Zabezpečení založené na rolích je zvlášť vhodné pro použití ve webových aplikacích v ASP.NET, které se zpracovávají hlavně na serveru. Zabezpečení založené na rolích .NET ale můžete použít buď na straně klienta, nebo na serveru.  
  
 Před čtením této části se ujistěte, že rozumíte materiálům uvedeným v tématu [klíčové koncepty zabezpečení](key-security-concepts.md).  
  
## <a name="see-also"></a>Viz také
  
- [Objekty zabezpečení a identity](principal-and-identity-objects.md)
- [Klíčové koncepty zabezpečení](key-security-concepts.md)
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
- [ASP.NET Core zabezpečení](/aspnet/core/security/)
