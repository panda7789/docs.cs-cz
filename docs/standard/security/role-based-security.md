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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 596165bfac9c65898448714a4477b7f045bd87d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018577"
---
# <a name="role-based-security"></a>Zabezpečení na základě rolí
Role se často používají ve finančních nebo podnikových aplikací k vynucení zásad. Aplikace může například uložit omezení velikosti transakce zpracovávána v závislosti na tom, jestli uživatel, který zadal žádost je členem zadané roli. Úředníci může mít autorizaci k provádění transakcí, které jsou menší než zadaná prahová hodnota, vedoucí mohou mít vyšší limit a náměstek prezidentů může mít stále vyšší limit (nebo vůbec žádné omezení). Zabezpečení na základě rolí lze také pokud aplikace vyžaduje více schválení cílem udělat nějakou akci. Takovém případě může být nákupu systému, ve kterém můžete vygenerovat každý zaměstnanec žádost o nákupu, ale pouze nákupního můžete převést tuto žádost nákupní objednávka, kterou je možné odeslat do jiného dodavatele.  
  
 Zabezpečení na základě rolí rozhraní .NET framework podporuje autorizace tak, že informace o zabezpečení, která je vytvořená z přidružených identity, k dispozici pro aktuální vlákno. Identitu (a instanční objekt, který pomáhá definovat) může být buď založené na účtu Windows nebo vlastní identitou nesouvisí se účet Windows. Aplikace rozhraní .NET framework můžete rozhodovat autorizace na základě daného objektu zabezpečení identity nebo členství v roli nebo obojí. Role je pojmenovaná sada objektů zabezpečení, které mají stejná oprávnění s ohledem na zabezpečení (například pokladní nebo manažera). Objekt zabezpečení může být členem jedné nebo více rolí. Aplikace proto můžete použít členství v rolích k určení, zda je objekt oprávnění k provedení požadované akce.  
  
 Snadné použití a konzistence poskytnout zabezpečení přístupu kódu, zabezpečení na základě rolí rozhraní .NET Framework poskytuje <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> objekty, které umožňují modul common language runtime k autorizaci způsobem, který je podobný kód přístup k kontroly zabezpečení. <xref:System.Security.Permissions.PrincipalPermission> Třída reprezentuje identitu nebo roli, které objektu zabezpečení musí odpovídat a je kompatibilní s kontrolami deklarativního a imperativního zabezpečení. Můžete také získat přímo přístup k informace o identitě daného objektu zabezpečení a provádění role a identity, zkontroluje ve vašem kódu v případě potřeby.  
  
 .NET Framework poskytuje podporu zabezpečení na základě rolí, který je dostatečně flexibilní a rozšiřitelné podle potřeb široké spektrum aplikací. Můžete vybrat pro spolupráci se stávající infrastrukturou ověřování, jako jsou služby COM + 1.0, nebo k vytvoření vlastního ověřovacího systému. Zabezpečení na základě role je zvlášť vhodné pro použití ve webových aplikacích ASP.NET, které jsou zpracovány primárně na serveru. Zabezpečení na základě rolí rozhraní .NET Framework je však možné u klienta nebo serveru.  
  
 Před čtením této části, ujistěte se, že rozumíte materiály uvedené v [klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)|Vysvětluje, jak nastavit a spravovat Windows a obecné identity a objekty zabezpečení.|  
|[Klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md)|Představuje základní koncepty, které je třeba porozumět před použitím zabezpečení rozhraní .NET Framework.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
