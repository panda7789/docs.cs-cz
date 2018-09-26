---
title: Důležité informace o zabezpečení pro zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
author: BrucePerlerMS
ms.openlocfilehash: 470ffc007ed73b28beba24bd0eb9c670dea9337d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199967"
---
# <a name="security-considerations-for-secure-sessions"></a>Důležité informace o zabezpečení pro zabezpečené relace
Měli byste zvážit následující položky, které mají vliv na zabezpečení při provádění zabezpečených relací. Další informace o aspektech týkajících se zabezpečení najdete v tématu [aspekty zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) a [osvědčené postupy pro zabezpečení](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Zabezpečené relace a metadat  
 Při vytvoření zabezpečené relace a <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> je nastavena na `false`, odešle Windows Communication Foundation (WCF) `mssp:MustNotSendCancel` kontrolní výraz jako součást metadat v dokumentu webové služby WSDL (Description Language) pro koncový bod služby. `mssp:MustNotSendCancel` Kontrolní výraz informuje klienty, že služba nereaguje na požadavků pro zrušení zabezpečenou relaci. Když <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> je nastavena na `true`, pak WCF negeneruje `mssp:MustNotSendCancel` kontrolního výrazu v dokumentu WSDL. Klienti se očekává odeslat požadavek na zrušení služby, pokud se už nevyžadují zabezpečenou relaci. Když klient je generována pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), kód klienta správně reaguje na přítomnosti nebo nepřítomnosti `mssp:MustNotSendCancel` kontrolní výraz.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Zabezpečené konverzace a vlastní tokeny  
 Existují některé problémy s kombinováním vlastní tokeny a odvozených klíčů kvůli způsobu, jakým je definováno ve specifikaci WS-SecureConversation. Specifikace, která uvádí `wsse:SecurityTokenReference` je volitelný prvek, který odkazuje na token odvozeného: "`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` tento volitelný prvek slouží k určení tokenu kontextu zabezpečení, token zabezpečení nebo sdílený klíč a tajný klíč používaný pro odvození. Pokud není zadán, předpokládá se, že příjemce může určit sdílený klíč z kontextu zprávy. Pokud nelze určit kontext, pak selhání, jako `wsc:UnknownDerivationSource` by měla být zvýšena. "  
  
 To znamená, že pokud chcete vlastní token nelze odvodit, měly sbalit její typ klauzuli v `SecurityTokenReference` elementu. Možnost vypnout odvození, ale výchozí hodnota je pro odvození klíče. Pokud převezmete služby při zabalení klíče, serializaci token odvozeného klíče proběhne úspěšně, ale pokus o deserializaci ji vyvolá výjimku.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Zakázání zabezpečených relací u WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Osvědčené postupy pro zabezpečení](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
