---
title: Zabezpečení na základě rolí
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
ms.openlocfilehash: 1dfb1f6246e86d6f565c9338fb09f34a1608e9b0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705922"
---
# <a name="role-based-security"></a>Zabezpečení na základě rolí
Role se často používají ve finančních nebo obchodních aplikacích k vymáhání zásad. Například aplikace může stanovit omezení velikosti zpracovávané transakce v závislosti na tom, zda uživatel, který požadavek odeslal, je členem zadané role. Přípravci můžou mít autorizaci pro zpracování transakcí, které jsou menší než zadané prahové hodnoty, můžou mít vedoucí vyšší limit a místopředsedé můžou mít pořád vyšší limit (nebo vůbec neplatí žádné omezení). Zabezpečení na základě rolí lze použít také v případě, že aplikace vyžaduje více schválení pro dokončení akce. Takový případ může být nákupní systém, ve kterém může kterýkoli zaměstnanec vygenerovat žádost o nákup, ale jenom pro nákupního agenta může tuto žádost převést na nákupní objednávku, kterou je možné odeslat dodavateli.  
  
 .NET Framework zabezpečení založené na rolích podporuje autorizaci pomocí informací o objektu zabezpečení, který je vytvořen z přidružené identity, který je k dispozici pro aktuální vlákno. Identitu (a objekt zabezpečení, který pomáhá definovat), může být buď založen na účtu systému Windows, nebo se jednat o vlastní identitu, která se nevztahuje k účtu systému Windows. .NET Framework aplikace mohou provádět rozhodnutí o autorizaci na základě identity nebo členství v roli objektu zabezpečení nebo obojího. Role je pojmenovaná sada objektů zabezpečení, které mají stejná oprávnění s ohledem na zabezpečení (například správce oznámení nebo správce). Objekt zabezpečení může být členem jedné nebo více rolí. Proto mohou aplikace použít členství v rolích k určení, zda je objekt zabezpečení autorizován k provedení požadované akce.  
  
 Pro zajištění snadného použití a konzistence se zabezpečením přístupu kódu .NET Framework zabezpečení na základě rolí poskytuje <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> objekty, které umožňují společnému jazykovým modulům runtime provádět autorizaci způsobem, který je podobný kontrole zabezpečení přístupu kódu. Třída <xref:System.Security.Permissions.PrincipalPermission> představuje identitu nebo roli, které musí objekt zabezpečení souhlasit a je kompatibilní s deklarativními a imperativními kontrolami zabezpečení. K informacím o identitě objektu zabezpečení můžete také přistupovat přímo a v případě potřeby provádět kontroly rolí a identit v kódu.  
  
 .NET Framework poskytuje podporu zabezpečení na základě rolí, která je flexibilní a rozšiřitelná tak, aby vyhovovala potřebám spektra aplikací. Můžete se rozhodnout, že budete spolupracovat se stávajícími ověřovacími infrastrukturami, jako jsou služby COM+ 1,0, nebo vytvořit vlastní ověřovací systém. Zabezpečení založené na rolích je zvlášť vhodné pro použití ve webových aplikacích v ASP.NET, které se zpracovávají hlavně na serveru. .NET Framework zabezpečení založené na rolích ale můžete použít buď na straně klienta, nebo na serveru.  
  
 Před čtením této části se ujistěte, že rozumíte materiálům uvedeným v tématu [klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)|Vysvětluje, jak nastavit a spravovat jak Windows, tak i obecné identity a objekty zabezpečení.|  
|[Klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md)|Představuje základní koncepty, které je nutné před použitím .NET Framework zabezpečení pochopit.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
