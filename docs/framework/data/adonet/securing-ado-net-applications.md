---
title: "Zabezpečení aplikací ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0424a92f2308c21404cf35cd59c797498e6af992
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="securing-adonet-applications"></a>Zabezpečení aplikací ADO.NET
Zápis zabezpečené aplikace ADO.NET zahrnuje více než zabraňující běžné kódování nástrahy například není ověřování uživatelského vstupu. Aplikace, která přistupuje k datům má mnoho potenciální body selhání, které může útočník zneužít k načtení, manipulaci nebo destroy citlivá data. Proto je důležité si uvědomit, všechny aspekty zabezpečení, z procesu modelování během fáze návrhu vaší aplikace, jeho případné nasazení a následné údržbě hrozeb.  
  
 Rozhraní .NET Framework poskytuje mnoho užitečných tříd, služby a nástroje pro zabezpečení a správě databázových aplikací. Modul CLR (CLR) poskytuje prostředí pro kód pro spuštění, se zabezpečení přístupu kódu (CAS) dále omezit oprávnění spravovaného kódu a bezpečnost typů. Následující data zabezpečeného přístupu kódování postupy omezuje škody, které může být si způsobilo potenciálním útočníkům.  
  
 Psaní kódu zabezpečené není chránit proti samo celistvosti při práci s nespravovaných prostředků, jako jsou třeba databáze. Většina databáze serveru, jako je SQL Server, mají vlastní systémy zabezpečení, které vylepšují zabezpečení, když je implementovaná správně. Ale i k datovému zdroji prostřednictvím systému robustní zabezpečení můžete obětí při útoku, pokud není správně nakonfigurován.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled zabezpečení](../../../../docs/framework/data/adonet/security-overview.md)  
 Poskytuje doporučení pro navrhování zabezpečených aplikací ADO.NET.  
  
 [Zabezpečený přístup k datům](../../../../docs/framework/data/adonet/secure-data-access.md)  
 Popisuje, jak pracovat s daty ze zdroje zabezpečená data.  
  
 [Zabezpečené klientské aplikace](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 Popisuje důležité informace o zabezpečení pro klientské aplikace.  
  
 [Zabezpečení přístupu ke kódu a ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)  
 Popisuje, jak certifikační Autority může pomoct chránit kód ADO.NET. Také popisuje, jak pracovat s částečnou důvěryhodností.  
  
 [Ochrana osobních údajů a zabezpečení dat](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 Popisuje možnosti šifrování pro technologii ADO.NET aplikace.  
  
## <a name="related-sections"></a>Související oddíly  
 [SQL Server – zabezpečení](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 Popisuje funkce zabezpečení systému SQL Server z hlediska pro vývojáře.  
  
 [Důležité informace o zabezpečení](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 Popisuje zabezpečení pro aplikace rozhraní Entity Framework.  
  
 [Zabezpečení](../../../../docs/standard/security/index.md)  
 Obsahuje odkazy na témata s popisem všechny aspekty zabezpečení v rozhraní .NET Framework.  
  
 [Nástroje zabezpečení](http://msdn.microsoft.com/en-us/2a3eb98a-2de6-4fba-b41c-01a74d354c11)  
 Rozhraní .NET framework – nástroje pro zabezpečení a správu zásad zabezpečení.  
  
 [Prostředky pro vytvoření zabezpečených aplikací](http://msdn.microsoft.com/en-us/0ebf5f69-76f2-498a-a2df-83cf3443e132)  
 Poskytuje odkazy na témata pro vytváření zabezpečených aplikací.  
  
 [Bibliografie k zabezpečení](/visualstudio/ide/security-bibliography)  
 Obsahuje odkazy na externí zdroje, které jsou k dispozici online a v tisku.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
