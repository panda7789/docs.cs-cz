---
title: Načítání informací nastavení z domény aplikace
description: Načtěte informace o instalaci z domény aplikace v rozhraní .NET pomocí třídy System. AppDomain nebo objektu AppDomainSetup.
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
ms.openlocfilehash: 06bf6b5901736b87852492f48a9d8972490b8304
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903464"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a>Načítání informací nastavení z domény aplikace
Každá instance domény aplikace se skládá z vlastností a <xref:System.AppDomainSetup> informací. Můžete načíst informace o instalaci z domény aplikace pomocí <xref:System.AppDomain?displayProperty=nameWithType> třídy. Tato třída poskytuje několik členů, kteří načítají konfigurační informace o doméně aplikace.  
  
 Můžete také zadat dotaz na objekt **AppDomainSetup** pro doménu aplikace, abyste získali informace o nastavení, které byly předány doméně při jejím vytvoření.  
  
 Následující příklad vytvoří novou doménu aplikace a následně vytiskne několik hodnot členů do konzoly.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 Následující příklad nastaví a následně načte informace o nastavení pro doménu aplikace. Všimněte si, že `AppDomain.SetupInformation.ApplicationBase` získá informace o konfiguraci.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Programování s aplikačními doménami](application-domains.md#programming-with-application-domains)
- [Používání domén aplikací](use.md)
