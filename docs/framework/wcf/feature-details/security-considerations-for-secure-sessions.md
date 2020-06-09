---
title: Důležité informace o zabezpečení pro zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
ms.openlocfilehash: 587897cc296523e0bfd5a4d4fa50b1e145cb69fb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601046"
---
# <a name="security-considerations-for-secure-sessions"></a>Důležité informace o zabezpečení pro zabezpečené relace
Při implementaci zabezpečených relací byste měli vzít v úvahu následující položky, které mají vliv na zabezpečení. Další informace o bezpečnostních faktorech najdete v tématu [požadavky na zabezpečení](security-considerations-in-wcf.md) a [osvědčené postupy pro zabezpečení](best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Zabezpečené relace a metadata  
 Když je navázána zabezpečená relace a <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> vlastnost je nastavena na `false` , Windows Communication Foundation (WCF) odešle `mssp:MustNotSendCancel` kontrolní výraz jako součást METADAT v dokumentu WSDL (Web Services Description Language) pro koncový bod služby. `mssp:MustNotSendCancel`Kontrolní výraz informuje klienty, že služba nereaguje na požadavky na zrušení zabezpečené relace. Pokud <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> je vlastnost nastavena na `true` , pak WCF negeneruje `mssp:MustNotSendCancel` kontrolní výraz v dokumentu WSDL. U klientů se očekává, že pošle žádost o zrušení do služby, když už nevyžadují zabezpečenou relaci. Když se klient generuje pomocí nástroje pro dokládání [metadat (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md), kód klienta se znovu chová pro přítomnost nebo absence `mssp:MustNotSendCancel` kontrolního výrazu.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Zabezpečené konverzace a vlastní tokeny  
 Existují některé problémy se kombinováním vlastních tokenů a odvozených klíčů z důvodu způsobu, jakým je definován ve specifikaci WS-SecureConversation. Specifikace říká, že `wsse:SecurityTokenReference` je volitelný prvek, který odkazuje na odvozený token: " `/wsc:DerivedKeyToken/wsse:SecurityTokenReference` Tento volitelný element se používá k určení tokenu kontextu zabezpečení, tokenu zabezpečení nebo sdíleného klíče nebo tajného klíče použitého pro odvození. Pokud není zadaný, předpokládá se, že příjemce může určit sdílený klíč z kontextu zprávy. Pokud kontext nelze určit, je třeba vyvolat chybu, například `wsc:UnknownDerivationSource` . "  
  
 To znamená, že pokud požadujete odvození vlastního tokenu, měli byste v elementu zabalit jeho typ klauzule `SecurityTokenReference` . Existuje možnost vypnout odvození, ale výchozí hodnota je odvození klíčů. Pokud nezabalíte klíč, bude serializace tokenu odvozeného klíče úspěšná, ale pokus o jeho deserializaci vyvolá výjimku.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Otázky zabezpečení](security-considerations-in-wcf.md)
- [Osvědčené postupy pro zabezpečení](best-practices-for-security-in-wcf.md)
