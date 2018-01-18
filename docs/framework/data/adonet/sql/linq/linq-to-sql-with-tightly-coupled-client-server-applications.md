---
title: "Technologie LINQ to SQL s aplikacemi úzce párované Klient Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6ff0ee9019f8c61ad2fc18c5d22240abb2dc6b9b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>Technologie LINQ to SQL s aplikacemi úzce párované Klient Server
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]můžete používat ve střední vrstvě pro úzce párované inteligentní klienty na prezentační vrstvy. Ve scénářích, které se týkají přístupu k datům jen pro čtení, žádné kontroly optimistickou metodu souběžného nebo optimistickou metodu souběžného časová razítka není mnohem složitější než v případě jiných vzdálené. Ale když databáze vyžaduje optimistickou metodu souběžného kontroluje s původní hodnoty [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] neposkytuje úroveň podpory pro odezvy dat, které můžete najít v datových sadách. Ale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] střední vrstvy můžou vyměňovat data s klienty na jakékoli platformě.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]v [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] poskytuje žádnou infrastrukturu pro sledování stavu entity po mít byl serializován do klienta. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Umožňuje kde interakce mezi data a prezentační vrstvy jsou malé a relativně atomic architektury orientované na služby, ale neprovádí žádné odezvy původní hodnoty. Proto pokud budete chtít použít úzce párované inteligentní klienta s [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]a databáze používá optimistickou metodu souběžného s původní hodnoty, je nutné implementovat vlastní mechanismus pro komunikaci mezi prezentační vrstvou a střední změny úroveň. Je až návrháři se rozhodnout, zda má smysl udělat tento bit další práci za výhody [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje ve střední vrstvě. Na druhé straně Pokud databáze obsahuje časová razítka, nejsou pro vlastní logiky sledování změn není nutné.  
  
## <a name="see-also"></a>Viz také  
 [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [N-vrstvé nastavení LINQ to SQL s webovými službami](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [Práce s datovými sadami ve vícevrstvých aplikacích](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)
