---
title: "Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: e230c02d53f8222034dfd79872cde9c540c31963
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zahrnuje několik vazeb poskytovaných systémem, které lze konfigurovat, ale neposkytuje úplnou flexibilitu při konfiguraci všech zabezpečení možnostech, které [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje. Toto téma ukazuje, jak vytvořit vlastní vazby přímo z jednotlivých vazby elementů a zvýrazňuje některé z nastavení zabezpečení, které je možné zadat při vytváření takovou vazbu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vytváření vlastních vazeb, najdete v části [rozšíření vazby](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
> [!WARNING]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement>nepodporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> kanálu tvar, který se používá výchozí kanál obrazce pomocí protokolu TCP při přenosu <xref:System.ServiceModel.TransferMode> je nastaven na <xref:System.ServiceModel.TransferMode.Buffered>. Je nutné nastavit <xref:System.ServiceModel.TransferMode> k <xref:System.ServiceModel.TransferMode.Streamed> Chcete-li použít <xref:System.ServiceModel.Channels.SecurityBindingElement> v tomto scénáři.  
  
## <a name="creating-a-custom-binding"></a>Vytvoření vlastní vazby  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] všechny vazby jsou tvořeny *elementů vazby*. Každý prvek vazba je odvozena z <xref:System.ServiceModel.Channels.BindingElement> třídy. Pro standardní vazby poskytované systémem prvky vazby vytvoříte a nakonfigurujete, i když můžete přizpůsobit některé z nastavení vlastností.  
  
 Naproti tomu Pokud chcete vytvořit vlastní vazby, prvky vazeb vytvoříte a nakonfigurujete a <xref:System.ServiceModel.Channels.CustomBinding> je vytvořený z elementů vazby.  
  
 K tomu, přidáte do kolekce reprezentována instanci prvky jednotlivé vazby <xref:System.ServiceModel.Channels.BindingElementCollection> a poté nastavit `Elements` vlastnost `CustomBinding` rovná tohoto objektu. Je nutné přidat prvky vazby v následujícím pořadí: toku transakcí, spolehlivé relace, zabezpečení, složené duplexní, jednosměrné, zabezpečení datového proudu, kódování zpráv a přenosu. Všimněte si, že ne všechny prvky vazby uvedené jsou potřeba v každé vazby.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Tři prvky vazeb se týkají úrovně zabezpečení zpráv, které dědí z <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy. Jsou tři <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Slouží k poskytování zabezpečení smíšeného režimu. Další dva elementy se používají při vrstvě zpráv poskytuje zabezpečení.  
  
 Další třídy se používají, když je k dispozici zabezpečení na úrovni přenosu:  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Požadované elementů vazby  
 Existuje velký počet prvky možné vazby, které lze spojit do vazbu. Ne všechny tyto kombinace jsou platné. V této části popisuje požadované prvky, které musí být v vazby zabezpečení.  
  
 Vazby platný zabezpečení závisí na mnoha faktorech, včetně následujících:  
  
-   Režim zabezpečení.  
  
-   Přenosový protokol.  
  
-   Vzorce výměny zpráv (MEP) uvedených ve smlouvě.  
  
 Následující tabulka uvádí konfigurace zásobníku element platnou vazbu pro každou kombinaci předchozí faktorů. Všimněte si, že jsou minimální požadavky. Prvky vazeb další můžete přidat k vazba, jako je například prvky vazby, prvky vazeb transakce a další prvky vazby kódování zprávy.  
  
|Režim zabezpečení.|Přenos|Kontrakt vzorce výměny zpráv|Kontrakt vzorce výměny zpráv|Kontrakt vzorce výměny zpráv|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Přenos|protokol HTTPS||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||Protokol SSL nebo Windows StreamSecurityBindingElement|Protokol SSL nebo Windows StreamSecurityBindingElement|Protokol SSL nebo Windows StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Zpráva|http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|Prvek SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||TCP|SecurityBindingElement|SecurityBindingElement|Prvek SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Smíšená (přenosu s pověřením zpráv)|protokol HTTPS|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|Prvek SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|Prvek SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|  
|||OneWayBindingElement|||  
|||Protokol SSL nebo Windows StreamSecurityBindingElement|Protokol SSL nebo Windows StreamSecurityBindingElement|Protokol SSL nebo Windows StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 Všimněte si, že jsou mnoho konfigurovat nastavení na SecurityBindingElements. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Zabezpečené konverzace a zabezpečené relace](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>Vytvoření vlastní vazby, který používá třídu SymmetricSecurityBindingElement  
  
1.  Vytvoření instance <xref:System.ServiceModel.Channels.BindingElementCollection> třída s názvem `outputBec`.  
  
2.  Zavolejte statickou metodu `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`, které vrací instanci třídy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> třídy.  
  
3.  Přidat <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> do kolekce (`outputBec`) voláním `Add` metodu <xref:System.Collections.ObjectModel.Collection%601> z <xref:System.ServiceModel.Channels.BindingElement> třídy.  
  
4.  Vytvoření instance <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> třídu a přidejte ji do kolekce (`outputBec`). Určuje kódování použité vazbou.  
  
5.  Vytvoření <xref:System.ServiceModel.Channels.HttpTransportBindingElement> a přidejte ji do kolekce (`outputBec`). Určuje, že vazba používá přenos HTTP.  
  
6.  Vytvoření nové vlastní vazby tak, že vytvoříte instanci <xref:System.ServiceModel.Channels.CustomBinding> třídy a předávání kolekce `outputBec` konstruktoru.  
  
7.  Výsledná vazba vlastní celá řada stejné vlastnosti jako standardní <xref:System.ServiceModel.WSHttpBinding>. Určuje úroveň zprávy zabezpečení a přihlašovací údaje systému Windows, ale zakáže zabezpečených relací, vyžaduje, aby přihlašovací údaje služby zadaný out-of-band a podpisy, nešifruje. Poslední se dá nastavit jenom podle nastavení <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> vlastnost, jak je znázorněno v kroku 4. Další dvě se dá řídit pomocí nastavení na standardní vazby.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad obsahuje kompletní funkci pro vytvoření vlastní vazby, který používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
### <a name="code"></a>Kód  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Rozšíření vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
