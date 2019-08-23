---
title: Zabezpečení aplikací ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: d4c9c21f4d1f4a08ca6d676ee7b4c9e80709ba19
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963124"
---
# <a name="securing-adonet-applications"></a>Zabezpečení aplikací ADO.NET
Zápis zabezpečené aplikace ADO.NET zahrnuje víc než vyhnout se běžnému kódování nástrah, jako je třeba ověřování vstupu uživatele. Aplikace, která přistupuje k datům, má mnoho potenciálních bodů selhání, které může útočník zneužít k načítání citlivých dat, manipulaci s nimi nebo jejich zničení. Proto je důležité porozumět všem aspektům zabezpečení, a to od procesu modelování hrozeb během fáze návrhu vaší aplikace až po její případné nasazení a průběžnou údržbu.  
  
 .NET Framework poskytuje spoustu užitečných tříd, služeb a nástrojů pro zabezpečení a správu databázových aplikací. Modul CLR (Common Language Runtime) poskytuje typově bezpečné prostředí pro kód, který se má spustit v rámci, s použitím zabezpečení přístupu kódu (CAS) k omezení dalších oprávnění spravovaného kódu. Následující postupy zabezpečení přístupu k datům omezují škodu, která může být způsobena potenciálním útočníkem.  
  
 Při práci s nespravovanými prostředky, jako jsou databáze, nechrání zabezpečený kód bezpečnostní otvory způsobené držiteli. Většina databází serveru, například SQL Server, má vlastní systémy zabezpečení, které zvyšují zabezpečení při správném implementaci. I když není správně nakonfigurovaný, může být i zdroj dat s robustním systémem zabezpečení obětí útoku.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled zabezpečení](../../../../docs/framework/data/adonet/security-overview.md)  
 Poskytuje doporučení pro navrhování zabezpečených aplikací ADO.NET.  
  
 [Zabezpečený přístup k datům](../../../../docs/framework/data/adonet/secure-data-access.md)  
 Popisuje, jak pracovat s daty ze zabezpečeného zdroje dat.  
  
 [Zabezpečené klientské aplikace](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 Popisuje požadavky na zabezpečení pro klientské aplikace.  
  
 [Zabezpečení přístupu ke kódu a ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)  
 Popisuje, jak mohou certifikační autority přispět k ochraně kódu ADO.NET. Také popisuje, jak pracovat s částečnou důvěryhodností.  
  
 [Ochrana osobních údajů a zabezpečení dat](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 Popisuje možnosti šifrování pro aplikace ADO.NET.  
  
## <a name="related-sections"></a>Související oddíly  
 [SQL Server – zabezpečení](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 Popisuje SQL Server funkce zabezpečení z pohledu vývojáře.  
  
 [Důležité informace o zabezpečení](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 Popisuje zabezpečení pro Entity Framework aplikace.  
  
 [Zabezpečení](../../../standard/security/index.md)  
 Obsahuje odkazy na témata popisující všechny aspekty zabezpečení v rozhraní .NET.  
  
 [Nástroje zabezpečení](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))  
 .NET Framework nástroje pro zabezpečení a správu zásad zabezpečení.  
  
 [Zdroje informací pro vytváření zabezpečených aplikací](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))  
 Obsahuje odkazy na témata týkající se vytváření zabezpečených aplikací.  
  
 [Bibliografie k zabezpečení](/visualstudio/ide/security-bibliography)  
 Poskytuje odkazy na externí prostředky dostupné online a v tisku.  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
