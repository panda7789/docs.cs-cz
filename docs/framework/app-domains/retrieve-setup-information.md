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
ms.openlocfilehash: 6fab54080a529a9b5a93c06a4f249a9c14ecd7af
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-setup-information-from-an-application-domain"></a>Načítání informací nastavení z domény aplikace
Každá instance domény aplikace se skládá z obě vlastnosti a <xref:System.AppDomainSetup> informace. Informace o instalaci můžete načíst z domény aplikace pomocí <xref:System.AppDomain?displayProperty=nameWithType> třídy. Tato třída poskytuje několik členů, kteří získávají informace o konfiguraci o domény aplikace.  
  
 Můžete taky zadat dotaz **AppDomainSetup** objekt pro doménu aplikace pro získání informací o nastavení, který byl předán do domény, pokud byla vytvořena.  
  
 Následující příklad vytvoří novou doménu aplikace a potom zobrazí několik hodnoty členů do konzoly.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 Následující příklad sady a potom načte, informace o nastavení domény aplikace. Všimněte si, že `AppDomain.SetupInformation.ApplicationBase` získá informace o konfiguraci.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Programování s doménami aplikací](application-domains.md#programming-with-application-domains)  
 [Používání domén aplikací](../../../docs/framework/app-domains/use.md)
