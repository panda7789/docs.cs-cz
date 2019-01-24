---
title: '&lt;claimTypeRequirements&gt; pro &lt;message&gt;'
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: 5c2bc05887701e78335629a37ce82815ac9abda5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628862"
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a>&lt;claimTypeRequirements&gt; pro &lt;message&gt;
Určuje kolekci požadovaných typů deklarací.  
  
 Kolekce slouží ve službě k určení požadovaných a volitelných deklarací, které musí být v vydaný token, který klient používá pro přístup ke službě. Služba zveřejňuje typy požadovaná deklarace identity v metadatech, pokud je povoleno publikování WSDL, ale WCF nevyžaduje, aby vydaný token obsahují typy, které žádost. Služby, které chtějí vynutit požadovaná deklarace identity, že typy jsou k dispozici by měl provést pomocí zásad autorizace.  
  
 U federovaných klientů Tato kolekce obsahuje seznam povinných a volitelných deklarací identity, která se posílají ve službě security token v požadavku klienta pro vydaný token.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
