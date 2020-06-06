---
title: <claimTypeRequirements>for<message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: db6717022bf3af0c4922818668595dd3937e9c71
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704404"
---
# <a name="claimtyperequirements-for-message"></a>\<claimTypeRequirements>for\<message>
Určuje kolekci požadovaných typů deklarací.  
  
 Služba tuto kolekci používá k určení požadovaných a volitelných deklarací identity, které musí být v vystaveném tokenu, který klient používá pro přístup ke službě. Služba zveřejňuje požadované typy deklarací identity v metadatech, pokud je povoleno publikování WSDL, ale WCF nevyžaduje, aby vydaný token obsahoval zadané typy deklarací identity. K dispozici jsou služby, které chtějí vymáhat požadované typy deklarací identity, a to pomocí zásad autorizace.  
  
 V federovaných klientech obsahuje tato kolekce seznam požadovaných a volitelných deklarací identity, které se odesílají do služby tokenu zabezpečení v žádosti klienta o vydaný token.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
