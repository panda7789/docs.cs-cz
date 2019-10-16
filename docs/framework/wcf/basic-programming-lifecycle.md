---
title: Základní programovací životní cyklus
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: fe578ba3c655c9c9ea8398b9b2e4d4f974153c8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320815"
---
# <a name="basic-programming-lifecycle"></a>Základní programovací životní cyklus
Windows Communication Foundation (WCF) umožňuje aplikacím komunikovat bez ohledu na to, jestli jsou ve stejném počítači, přes Internet nebo na různých aplikačních platformách. Toto téma popisuje úkoly, které jsou nutné k vytvoření aplikace WCF. Pracovní ukázkovou aplikaci najdete v tématu [Začínáme kurzu](getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Základní úlohy  
 Základní úkoly, které je potřeba provést, jsou v uvedeném pořadí:  
  
1. Definujte kontrakt služby. Kontrakt služby určuje podpis služby, data, která vyměňuje, a další smluvní požadovaná data. Další informace najdete v tématu [Navrhování kontraktů služby](designing-service-contracts.md).  
  
2. Implementujte kontrakt. Chcete-li implementovat kontrakt služby, vytvořte třídu, která implementuje kontrakt a určete vlastní chování, které má modul runtime mít. Další informace najdete v tématu [implementace kontraktů služeb](implementing-service-contracts.md).  
  
3. Nakonfigurujte službu zadáním koncových bodů a dalších informací o chování. Další informace najdete v tématu [Konfigurace služeb](configuring-services.md).  
  
4. Hostování služby. Další informace najdete v tématu [hostující služby](hosting-services.md).  
  
5. Sestavte klientskou aplikaci. Další informace najdete v tématu [sestavování klientů](building-clients.md).  
  
 I když se témata v této části řídí tímto pořadím, některé scénáře se na začátku nespustí. Pokud například chcete vytvořit klienta pro existující službu, začněte v kroku 5. Nebo pokud vytváříte službu, kterou budou používat jiní uživatelé, můžete přeskočit krok 5.  
  
 Jakmile se seznámíte s vývojem kontraktů služby, můžete si také přečíst [Úvod k rozšíření](introduction-to-extensibility.md). Pokud máte ve své službě problémy, podívejte se na [rychlý Start pro řešení potíží WCF](wcf-troubleshooting-quickstart.md) a podívejte se, jestli mají ostatní stejné nebo podobné problémy.  
  
## <a name="see-also"></a>Viz také:

- [Implementace kontraktů služeb](implementing-service-contracts.md)
