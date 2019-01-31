---
title: <claimTypeRequirements> pro <message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: 9cf77f6c026df5f78cc8ae6e6783e91f1c86e282
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256601"
---
# <a name="claimtyperequirements-for-message"></a>\<claimTypeRequirements > pro \<zpráva >
Určuje kolekci požadovaných typů deklarací.  
  
 Kolekce slouží ve službě k určení požadovaných a volitelných deklarací, které musí být v vydaný token, který klient používá pro přístup ke službě. Služba zveřejňuje typy požadovaná deklarace identity v metadatech, pokud je povoleno publikování WSDL, ale WCF nevyžaduje, aby vydaný token obsahují typy, které žádost. Služby, které chtějí vynutit požadovaná deklarace identity, že typy jsou k dispozici by měl provést pomocí zásad autorizace.  
  
 U federovaných klientů Tato kolekce obsahuje seznam povinných a volitelných deklarací identity, která se posílají ve službě security token v požadavku klienta pro vydaný token.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
