---
title: "Zabezpečení na základě rolí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 18b2883fd69f5cadf2fce3dc677e5d2b79806d0b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="role-based-security"></a>Zabezpečení na základě rolí
Role se často používají v finanční nebo obchodní aplikace k vynucení zásad. Aplikace může například uložit omezení na velikost zpracovávané v závislosti na tom, zda uživatel zadal žádost je členem zadané roli transakce. Úředníci mohou být autorizace k provádění transakcí, které jsou menší než zadaná prahová hodnota, vedoucí mohou mít vyšší limit a místopředsedové mohou mít stále vyšší limit (nebo vůbec žádné omezení). Na základě rolí zabezpečení mohou sloužit také pokud aplikace vyžaduje více schválení pro dokončení akce. Takovém případě může být nákupní systém, ve kterém můžete každý zaměstnanec generovat nákupní žádost, ale pouze nákupní agent můžete převést tuto žádost nákupní objednávka, který lze odeslat buď do jiného dodavatele.  
  
 Zabezpečení na základě rolí rozhraní .NET framework podporuje autorizaci tím, že informace o objekt, který je vytvořený z přidružených identity, k dispozici pro aktuální vlákno. Identitu (a objekt, který pomáhá definovat) může být buď založené na účet systému Windows nebo být vlastní identity, které nejsou na účet systému Windows. Aplikace rozhraní .NET framework můžete provést rozhodnutí o autorizaci na základě identity objektu zabezpečení nebo členství v rolích nebo obojí. Role je pojmenovanou sadu objektů, které mají stejná práva s ohledem na zabezpečení (například pokladní nebo správce). Objekt zabezpečení může být členem jedné nebo více rolí. Proto aplikace můžete použít členství v rolích k určení, zda objekt zabezpečení má oprávnění provést požadovanou akci.  
  
 Snadné použití a konzistence poskytnout zabezpečení přístupu kódu, zabezpečení na základě rolí rozhraní .NET Framework poskytuje <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> objekty, které umožňují modul common language runtime k autorizaci způsobem, který je podobný kódu přístup kontroly zabezpečení. <xref:System.Security.Permissions.PrincipalPermission> Třída reprezentuje identitu nebo roli, které objekt zabezpečení musí odpovídat a je kompatibilní s kontrolami deklarativní a naléhavé zabezpečení. Můžete také přímý přístup objektu zabezpečení informací o identitě a provádět role a identity zkontroluje ve vašem kódu v případě potřeby.  
  
 Rozhraní .NET Framework poskytuje podporu na základě rolí zabezpečení, který je flexibilní a rozšiřitelný dost pro potřeby široké spektrum aplikace. Můžete spolupracovat se stávající infrastrukturou ověřování, jako je například služby COM + 1.0, nebo vytvořte vlastní ověřování systému. Zabezpečení na základě role je zvlášť vhodné pro použití v aplikacích ASP.NET Web, které jsou zpracovávány především na serveru. Zabezpečení na základě rolí rozhraní .NET Framework však lze použít na klienta nebo serveru.  
  
 Před čtením této části, ujistěte se, že rozumíte materiálu uvedenému v [klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)|Vysvětluje, jak nastavit a spravovat Windows a obecné identity a objekty zabezpečení.|  
|[Klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md)|Představuje základní koncepty, které je třeba porozumět před použitím zabezpečení rozhraní .NET Framework.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
