---
title: Technologie LINQ to SQL s úzce Spárovanými klient-server
ms.date: 03/30/2017
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
ms.openlocfilehash: 9c36fc1f402d3791611af47a3a6d997db4f31167
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521877"
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>Technologie LINQ to SQL s úzce Spárovanými klient-server
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je možné ve střední vrstvě s úzce spárovanými inteligentní klienti v prezentační vrstvě. Ve scénářích, které se týkají přístupu k datům jen pro čtení, žádné kontroly optimistického řízení souběžnosti nebo optimistického řízení souběžnosti ovládacím prvkem časová razítka není větší složitostí oproti pomocí jiné vzdálené scénáře. Ale pokud databáze vyžaduje kontroly optimistického řízení souběžnosti s původní hodnoty [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] neposkytuje úroveň podpory pro dopad na dobu odezvy data, která nenajdete v datových sadách. Ale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] střední vrstvy si mohou vyměňovat data s klienty na libovolné platformě.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] v [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] poskytuje žádnou infrastrukturu pro sledování stavu entity po jejich byl serializován do klienta. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Umožňuje kde interakce mezi data a prezentační vrstvy jsou malé a relativně atomic architektury orientované na služby, ale neprovede žádné verzemi původní hodnoty. Proto pokud chcete používat inteligentní klienta s úzce spárovanými [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]a databázi používá optimistické řízení souběžnosti s původní hodnoty, budete muset implementovat vlastní mechanismus pro komunikaci mezi prezentační vrstvou a střední změny úroveň. Je až do návrháře systém se rozhodnout, zda je vhodné provést tento bit práce navíc výměnou za výhody [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje ve střední vrstvě. Na druhé straně Pokud databáze obsahuje časové razítko, pak není nutné pro vlastní logiku sledování změn.  
  
## <a name="see-also"></a>Viz také  
 [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [N-vrstvé nastavení LINQ to SQL s webovými službami](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [Práce s datovými sadami ve vícevrstvých aplikacích](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)
