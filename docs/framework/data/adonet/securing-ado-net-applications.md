---
title: Zabezpečení aplikací ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 32d3de15242aaf9cfacd9371289a5a0a675f884b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664191"
---
# <a name="securing-adonet-applications"></a>Zabezpečení aplikací ADO.NET
Vytváření zabezpečených aplikací ADO.NET zahrnuje více než jak se vyhnout běžným nástrahám psaní kódu, jako je například není ověřování uživatelského vstupu. Aplikace, která přistupuje k datům má mnoho potenciálních bodů selhání, které může útočník zneužít k načtení, manipulaci nebo zničit citlivá data. Proto je důležité Porozumějte všem jejich aspektům zabezpečení z procesu před internetovými útoky modelování během fáze návrhu vaší aplikace, pro jeho nasazení konečné a průběžnou péči.  
  
 Rozhraní .NET Framework poskytuje mnoho užitečných tříd, služby a nástroje pro zabezpečení a správu databázových aplikací. Common language runtime (CLR) poskytuje prostředí typově bezpečný kód ke spuštění, se zabezpečení přístupu kódu (CAS) pro další omezení oprávnění spravovaného kódu. Po zabezpečení dat omezuje přístup kódování škody, které může být způsobené potenciální útočníky.  
  
 Psaní bezpečného kódu není pomáhalo chránit před poškozují bezpečnostní díry při práci s nespravované prostředky, jako jsou databáze. Většina databází serveru, jako je SQL Server, mají vlastní systémy zabezpečení, které umožňuje zvýšit zabezpečení při správné implementaci. Ale i datovému zdroji prostřednictvím robustní zabezpečení systému můžete obětí útoku, pokud není správně nakonfigurován.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled zabezpečení](../../../../docs/framework/data/adonet/security-overview.md)  
 Poskytuje doporučení pro návrh zabezpečených aplikací ADO.NET.  
  
 [Zabezpečený přístup k datům](../../../../docs/framework/data/adonet/secure-data-access.md)  
 Popisuje, jak pracovat s daty ze zdroje zabezpečeným datům.  
  
 [Zabezpečené klientské aplikace](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 Popisuje aspekty zabezpečení pro klientské aplikace.  
  
 [Zabezpečení přístupu ke kódu a ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)  
 Popisuje, jak certifikačních Autorit může pomoci chránit kódu ADO.NET. Také popisuje, jak pracovat s částečnou důvěryhodností.  
  
 [Ochrana osobních údajů a zabezpečení dat](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 Popisuje možnosti šifrování pro aplikace, ADO.NET.  
  
## <a name="related-sections"></a>Související oddíly  
 [SQL Server – zabezpečení](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 Popisuje funkce zabezpečení produktu SQL Server z pohledu vývojáře.  
  
 [Důležité informace o zabezpečení](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 Popisuje zabezpečení pro aplikace Entity Framework.  
  
 [Zabezpečení](../../../../docs/standard/security/index.md)  
 Obsahuje odkazy na témata popisující všech aspektů zabezpečení v rozhraní .NET.  
  
 [Nástroje zabezpečení](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))  
 Rozhraní .NET framework – nástroje pro zabezpečení a správě zásad zabezpečení.  
  
 [Prostředky pro vytváření zabezpečených aplikací](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))  
 Obsahuje odkazy na témata pro vytváření zabezpečených aplikací.  
  
 [Bibliografie k zabezpečení](/visualstudio/ide/security-bibliography)  
 Obsahuje odkazy na externí prostředky, které jsou k dispozici online a v tisku.  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
