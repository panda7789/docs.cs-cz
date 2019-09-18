---
title: Načítání informací nastavení z domény aplikace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 719ea15de135d8bbeb7bb88ea3d5b5874e30b5d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053106"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a>Načítání informací nastavení z domény aplikace
Každá instance domény aplikace se skládá z vlastností a <xref:System.AppDomainSetup> informací. Můžete načíst informace o instalaci z domény aplikace pomocí <xref:System.AppDomain?displayProperty=nameWithType> třídy. Tato třída poskytuje několik členů, kteří načítají konfigurační informace o doméně aplikace.  
  
 Můžete také zadat dotaz na objekt **AppDomainSetup** pro doménu aplikace, abyste získali informace o nastavení, které byly předány doméně při jejím vytvoření.  
  
 Následující příklad vytvoří novou doménu aplikace a následně vytiskne několik hodnot členů do konzoly.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 Následující příklad nastaví a následně načte informace o nastavení pro doménu aplikace. Všimněte si `AppDomain.SetupInformation.ApplicationBase` , že získá informace o konfiguraci.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Programování s aplikačními doménami](application-domains.md#programming-with-application-domains)
- [Používání domén aplikací](use.md)
