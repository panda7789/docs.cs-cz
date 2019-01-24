---
title: 'Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
ms.openlocfilehash: 2c2aa5703e31b2529e0b98d909a763b8b4b23035
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576154"
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement
Windows Communication Foundation (WCF) zahrnuje několik vazeb poskytovaných systémem, které můžete konfigurovat, ale neposkytují úplnou flexibilitu při konfiguraci všechny možnosti zabezpečení, které podporuje WCF. Toto téma ukazuje, jak vytvořit vlastní vazbu přímo z elementů vazby jednotlivých a zvýrazní některá nastavení zabezpečení, které můžete nastavit při vytváření takovou vazbu. Další informace o vytváření vlastních vazeb naleznete v tématu [rozšíření vazby](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
> [!WARNING]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement> nepodporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> kanálu tvar, což je výchozí kanál tvar použití protokolu TCP při přenosu <xref:System.ServiceModel.TransferMode> je nastavena na <xref:System.ServiceModel.TransferMode.Buffered>. Je nutné nastavit <xref:System.ServiceModel.TransferMode> k <xref:System.ServiceModel.TransferMode.Streamed> Chcete-li použít <xref:System.ServiceModel.Channels.SecurityBindingElement> v tomto scénáři.  
  
## <a name="creating-a-custom-binding"></a>Vytvoření vlastní vazby  
 Ve službě WCF všechny vazby jsou tvořené *elementů vazby*. Každý element vazby je odvozen od <xref:System.ServiceModel.Channels.BindingElement> třídy. Pro standardní vazeb poskytovaných systémem elementů vazby se vytvoří a nakonfigurují automaticky, i když můžete přizpůsobit některé z nastavení vlastností.  
  
 Naproti tomu k vytvoření vlastní vazby, elementy vazby jsou vytvoření a konfiguraci a <xref:System.ServiceModel.Channels.CustomBinding> je vytvořený z elementů vazby.  
  
 K tomu přidat prvky jednotlivých vazby do kolekce reprezentována instance <xref:System.ServiceModel.Channels.BindingElementCollection> třídy a pak nastavte `Elements` vlastnost `CustomBinding` rovná tohoto objektu. Je nutné přidat prvky vazby v následujícím pořadí: Tok transakcí, stabilní relace, zabezpečení, kompozitní duplexní, jednosměrný Stream zabezpečení, kódování zpráv a přenosu. Všimněte si, že jsou všechny prvky vazby uvedené nezbytné Každá vazba.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Tři prvky vazby se vztahují k úrovni zabezpečení zpráv, které jsou odvozeny z <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy. Jsou tři <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Slouží k zajištění zabezpečení smíšeného režimu. Dva elementy se používají při vrstva zpráv poskytuje zabezpečení.  
  
 Další třídy se používají při zabezpečení na úrovni přenosu je k dispozici:  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Vyžaduje elementů vazby  
 Existuje velký počet vazeb prvky, které je možné kombinovat do vazby. Ne všechny tyto kombinace jsou platné. Tato část popisuje požadované prvky, které musí být součástí vazby zabezpečení.  
  
 Vazby zabezpečení platné závisí na mnoha faktorech, včetně následujících:  
  
-   Režim zabezpečení.  
  
-   Přenosový protokol.  
  
-   Vzorce výměny zpráv (MEP) uvedené ve smlouvě.  
  
 Následující tabulka uvádí konfigurace zásobníku element platnou vazbu pro každou kombinaci na předchozích faktorech. Všimněte si, že jsou minimální požadavky. Elementy další vazby můžete přidat do vazby, jako je například elementy vazby, transakce elementů vazby a další prvky vazby kódování zprávy.  
  
|Režim zabezpečení|Přenos|Kontrakt vzoru výměny zpráv|Kontrakt vzoru výměny zpráv|Kontrakt vzoru výměny zpráv|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Přenos|Https||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||Protokol SSL nebo třídu StreamSecurityBindingElement Windows|Protokol SSL nebo třídu StreamSecurityBindingElement Windows|Protokol SSL nebo třídu StreamSecurityBindingElement Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Zpráva|Http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|Element SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||Tcp|SecurityBindingElement|SecurityBindingElement|Element SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Smíšená (přenosu s přihlašovacími údaji zprávy)|Https|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|Element SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|Element SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|  
|||OneWayBindingElement|||  
|||Protokol SSL nebo třídu StreamSecurityBindingElement Windows|Protokol SSL nebo třídu StreamSecurityBindingElement Windows|Protokol SSL nebo třídu StreamSecurityBindingElement Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 Všimněte si, že existují mnoho konfigurovatelných nastavení na SecurityBindingElements. Další informace najdete v tématu [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 Další informace najdete v tématu [zabezpečené konverzace a zabezpečené relace](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>Vytvoření vlastní vazby, který používá třídu SymmetricSecurityBindingElement  
  
1.  Vytvoření instance <xref:System.ServiceModel.Channels.BindingElementCollection> třída s názvem `outputBec`.  
  
2.  Zavolejte statickou metodu `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`, která vrací instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> třídy.  
  
3.  Přidat <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> do kolekce (`outputBec`) voláním `Add` metodu <xref:System.Collections.ObjectModel.Collection%601> z <xref:System.ServiceModel.Channels.BindingElement> třídy.  
  
4.  Vytvoření instance <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> třídu a přidejte ho do kolekce (`outputBec`). Určuje kódování použité vazbou.  
  
5.  Vytvoření <xref:System.ServiceModel.Channels.HttpTransportBindingElement> a přidejte ho do kolekce (`outputBec`). Určuje, že vazba používá přenos pomocí protokolu HTTP.  
  
6.  Vytvořte novou vlastní vazbu tak, že vytvoříte instanci <xref:System.ServiceModel.Channels.CustomBinding> třídy a předávání kolekce `outputBec` konstruktoru.  
  
7.  Výsledný vlastní vazby sdílí řadu stejné vlastnosti jako standardní <xref:System.ServiceModel.WSHttpBinding>. Určuje zabezpečení na úrovni zpráv a přihlašovací údaje Windows, ale zakáže zabezpečených relací, vyžaduje, aby zadaný out-of-band, přihlašovací údaje služby a podpisy, nešifruje. Poslední se dá nastavit jenom podle nastavení <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> vlastnost, jak je znázorněno v kroku 4. Další dvě jako se dá řídit pomocí nastavení na standardní vazbu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad obsahuje kompletní funkce k vytvoření vlastní vazby, který používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
### <a name="code"></a>Kód  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Rozšíření vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
