---
title: "Důležité informace o zabezpečení pro zabezpečené relace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: be460249ed877b2f67f2d153c2aea4a3cc4d2b37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-for-secure-sessions"></a>Důležité informace o zabezpečení pro zabezpečené relace
Měli byste zvážit následující položky, které mají vliv na zabezpečení při implementaci zabezpečených relací. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]aspekty zabezpečení, najdete v části [aspekty zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) a [osvědčené postupy pro zabezpečení](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Zabezpečených relací a Metadata  
 Když je vytvořena zabezpečené relace a <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> je nastavena na `false`, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] odešle `mssp:MustNotSendCancel` assertion jako součást metadata v dokumentu webové služby popis Language (WSDL) pro koncový bod služby. `mssp:MustNotSendCancel` Kontrolní výraz informuje klientů, že služba nereaguje na žádosti o zrušení zabezpečené relace. Když <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> je nastavena na `true`, pak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] není emitování `mssp:MustNotSendCancel` assertion v souboru WSDL. Očekává se, že klienti odeslat žádost o zrušení ke službě, když už vyžadují zabezpečené relace. Když klient je generována pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), kód klienta správně reaguje na přítomnosti nebo absenci `mssp:MustNotSendCancel` kontrolní výraz.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Zabezpečené konverzace a vlastní tokeny  
 Existují některé problémy s kombinací vlastní tokeny a odvozené klíče z důvodu způsob, jakým je definována ve specifikaci WS-SecureConversation. Specifikace uvádí, že `wsse:SecurityTokenReference` je volitelný element, který odkazuje na odvozenou token: "`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` tento volitelný element se používá k určení tokenu kontextu zabezpečení, token zabezpečení nebo sdílený klíč nebo tajný klíč používaný pro odvození. Pokud není zadaný, předpokládá se, že příjemce můžete určit sdílený klíč z daného kontextu zprávy. Pokud nelze určit kontext, pak chybu, jako `wsc:UnknownDerivationSource` by měl být aktivována. "  
  
 To znamená, že pokud chcete vlastní token odvozeny, má obtékat klauzule typu v `SecurityTokenReference` elementu. Možnost vypnout odvození ale je ve výchozím nastavení se odvozují klíče. Pokud žádnou zabalení klíče, odvozené klíče tokenu úspěšné, ale při pokusu o deserializaci vyvolá výjimku.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Zakázání zabezpečených relací u WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Osvědčené postupy pro zabezpečení](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
