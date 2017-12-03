---
title: '&lt;claimTypeRequirements&gt; pro &lt;message&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 158aad6a6a11bb889df74e1222a8881a1c38803f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a>&lt;claimTypeRequirements&gt; pro &lt;message&gt;
Určuje kolekci typů požadované deklarace identity.  
  
 Kolekce se používá služba zadat všechny požadované a volitelné deklarace, které musí být v vydaných tokenu, které klient používá k přístupu ke službě. Službu zpřístupní typy požadované deklarací identity v metadatech, pokud je povoleno publikování WSDL ale WCF nevyžaduje vydaný token obsahovat typy zadaný deklarací identity. Služby, které chtějí vynutit požadované deklarace identity, zda jsou k dispozici typy by to pomocí zásad autorizace.  
  
 U federovaných klientů Tato kolekce obsahuje seznam požadované a volitelné deklarací identity, která se posílají služby tokenů zabezpečení v požadavku klienta u vydaných tokenu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
