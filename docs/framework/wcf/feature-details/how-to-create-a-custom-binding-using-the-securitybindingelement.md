---
title: 'Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
ms.openlocfilehash: 15fdd50b05bd2217cb9819373cd1c015da52b15b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599006"
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement
Windows Communication Foundation (WCF) zahrnuje několik systémových vazeb, které je možné nakonfigurovat, ale neposkytují plnou flexibilitu při konfiguraci všech možností zabezpečení, které podporuje WCF. Toto téma ukazuje, jak vytvořit vlastní vazbu přímo z jednotlivých prvků vazby a zvýrazní některá z nastavení zabezpečení, která lze zadat při vytváření takové vazby. Další informace o vytváření vlastních vazeb naleznete v tématu [rozšíření vazeb](../extending/extending-bindings.md).  
  
> [!WARNING]
> <xref:System.ServiceModel.Channels.SecurityBindingElement>nepodporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> obrazec kanálu, což je výchozí obrazec kanálu, který používá přenos TCP, pokud <xref:System.ServiceModel.TransferMode> je nastaven na <xref:System.ServiceModel.TransferMode.Buffered> . V tomto scénáři musíte nastavit na, aby <xref:System.ServiceModel.TransferMode> <xref:System.ServiceModel.TransferMode.Streamed> bylo možné použít <xref:System.ServiceModel.Channels.SecurityBindingElement> .  
  
## <a name="creating-a-custom-binding"></a>Vytvoření vlastní vazby  
 V WCF jsou všechny vazby tvořeny *prvky vazby*. Každý prvek vazby je odvozen z <xref:System.ServiceModel.Channels.BindingElement> třídy. Pro standardní systémové vazby se vytvoří a nakonfigurují prvky vazby, i když můžete přizpůsobit některá nastavení vlastností.  
  
 Naopak pro vytvoření vlastní vazby se vytvoří a nakonfigurují prvky vazby a vytvoří <xref:System.ServiceModel.Channels.CustomBinding> se z elementů vazby.  
  
 Chcete-li to provést, přidejte jednotlivé prvky vazby do kolekce reprezentované instancí <xref:System.ServiceModel.Channels.BindingElementCollection> třídy a pak nastavte `Elements` vlastnost `CustomBinding` objektu EQUAL. Je nutné přidat prvky vazby v následujícím pořadí: tok transakce, spolehlivé relace, zabezpečení, kompozitní duplexní, jednosměrné, zabezpečení datového proudu, kódování zpráv a přenos. Všimněte si, že ne všechny uvedené prvky vazby jsou požadovány při každé vazbě.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Tři prvky vazby se týkají zabezpečení na úrovni zprávy, z nichž všechny jsou odvozeny z <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy. Tři jsou <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> , <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> . <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>Slouží k zajištění zabezpečení smíšeného režimu. Další dva prvky jsou použity, když vrstva zprávy poskytuje zabezpečení.  
  
 Další třídy se používají v případě, že je zajištěno zabezpečení na úrovni přenosu:  
  
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Požadované prvky vazby  
 Existuje velký počet možných prvků vazby, které mohou být kombinovány do vazby. Některé z těchto kombinací nejsou platné. Tato část popisuje vyžadované prvky, které musí být přítomny ve vazbě zabezpečení.  
  
 Platné vazby zabezpečení závisí na mnoha faktorech, včetně následujících:  
  
- Režim zabezpečení.  
  
- Transportní protokol.  
  
- Vzor výměny zpráv (MEP) zadaný v kontraktu.  
  
 V následující tabulce jsou uvedeny platné konfigurace zásobníku prvků vazby pro každou kombinaci předchozích faktorů. Všimněte si, že se jedná o minimální požadavky. Do vazby lze přidat další prvky vazby, například prvky vazby kódování zprávy, prvky vazby transakce a jiné prvky vazby.  
  
|Režim zabezpečení|Přenos|Vzor výměny zpráv o kontraktu|Vzor výměny zpráv o kontraktu|Vzor výměny zpráv o kontraktu|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Přenos|Https||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||SSL nebo Windows třídu StreamSecurityBindingElement|SSL nebo Windows třídu StreamSecurityBindingElement|SSL nebo Windows třídu StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Zpráva|HTTP|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||Protokolu|SecurityBindingElement|SecurityBindingElement|SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Smíšený (přenos s přihlašovacími údaji zprávy)|Https|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|SymmetricSecurityBindingElement (režim ověřování = SecureConversation)|  
|||OneWayBindingElement|||  
|||SSL nebo Windows třídu StreamSecurityBindingElement|SSL nebo Windows třídu StreamSecurityBindingElement|SSL nebo Windows třídu StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 Všimněte si, že SecurityBindingElements má mnoho konfigurovatelných nastavení. Další informace najdete v tématu [režimy ověřování SecurityBindingElement](securitybindingelement-authentication-modes.md).  
  
 Další informace najdete v tématu [zabezpečené konverzace a zabezpečené relace](secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>Vytvoření vlastní vazby, která používá SymmetricSecurityBindingElement  
  
1. Vytvořte instanci <xref:System.ServiceModel.Channels.BindingElementCollection> třídy s názvem `outputBec` .  
  
2. Zavolejte statickou metodu `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)` , která vrátí instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> třídy.  
  
3. Přidejte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> do kolekce ( `outputBec` ) voláním `Add` metody <xref:System.Collections.ObjectModel.Collection%601> <xref:System.ServiceModel.Channels.BindingElement> třídy.  
  
4. Vytvořte instanci <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> třídy a přidejte ji do kolekce ( `outputBec` ). Toto určuje kódování používané vazbou.  
  
5. Vytvořte <xref:System.ServiceModel.Channels.HttpTransportBindingElement> a přidejte ho do kolekce ( `outputBec` ). Tím se určuje, že vazba používá přenos HTTP.  
  
6. Vytvořte novou vlastní vazbu vytvořením instance <xref:System.ServiceModel.Channels.CustomBinding> třídy a předáním kolekce `outputBec` do konstruktoru.  
  
7. Výsledná vlastní vazba sdílí mnoho stejných vlastností jako standard <xref:System.ServiceModel.WSHttpBinding> . Určuje zabezpečení na úrovni zprávy a přihlašovací údaje systému Windows, ale zakáže zabezpečené relace, vyžaduje, aby pověření služby bylo určeno mimo IP síť a nešifroval signatury. Poslední lze ovládat pouze nastavením <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> vlastnosti, jak je znázorněno v kroku 4. Ostatní dvě lze ovládat pomocí nastavení standardní vazby.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad poskytuje úplnou funkci pro vytvoření vlastní vazby, která používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .  
  
### <a name="code"></a>Kód  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Rozšíření vazeb](../extending/extending-bindings.md)
- [Vazby poskytované systémem](../system-provided-bindings.md)
