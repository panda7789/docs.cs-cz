---
title: Důležité informace o zabezpečení pro zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f4ee56204d6980f412b9781868714dedb3c2675c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="security-considerations-for-secure-sessions"></a>Důležité informace o zabezpečení pro zabezpečené relace
Měli byste zvážit následující položky, které mají vliv na zabezpečení při implementaci zabezpečených relací. Další informace o aspektech zabezpečení najdete v tématu [aspekty zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) a [osvědčené postupy pro zabezpečení](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Zabezpečených relací a Metadata  
 Když je vytvořena zabezpečené relace a <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> je nastavena na `false`, odešle Windows Communication Foundation (WCF) `mssp:MustNotSendCancel` assertion jako součást metadat v dokumentu webové služby popis Language (WSDL) koncový bod služby. `mssp:MustNotSendCancel` Kontrolní výraz informuje klientů, že služba nereaguje na žádosti o zrušení zabezpečené relace. Když <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> je nastavena na `true`, pak není emitování WCF `mssp:MustNotSendCancel` assertion v souboru WSDL. Očekává se, že klienti odeslat žádost o zrušení ke službě, když už vyžadují zabezpečené relace. Když klient je generována pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), kód klienta správně reaguje na přítomnosti nebo absenci `mssp:MustNotSendCancel` kontrolní výraz.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Zabezpečené konverzace a vlastní tokeny  
 Existují některé problémy s kombinací vlastní tokeny a odvozené klíče z důvodu způsob, jakým je definována ve specifikaci WS-SecureConversation. Specifikace uvádí, že `wsse:SecurityTokenReference` je volitelný element, který odkazuje na odvozenou token: "`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` tento volitelný element se používá k určení tokenu kontextu zabezpečení, token zabezpečení nebo sdílený klíč nebo tajný klíč používaný pro odvození. Pokud není zadaný, předpokládá se, že příjemce můžete určit sdílený klíč z daného kontextu zprávy. Pokud nelze určit kontext, pak chybu, jako `wsc:UnknownDerivationSource` by měl být aktivována. "  
  
 To znamená, že pokud chcete vlastní token odvozeny, má obtékat klauzule typu v `SecurityTokenReference` elementu. Možnost vypnout odvození ale je ve výchozím nastavení se odvozují klíče. Pokud žádnou zabalení klíče, odvozené klíče tokenu úspěšné, ale při pokusu o deserializaci vyvolá výjimku.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Zakázání zabezpečených relací u WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Osvědčené postupy pro zabezpečení](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
