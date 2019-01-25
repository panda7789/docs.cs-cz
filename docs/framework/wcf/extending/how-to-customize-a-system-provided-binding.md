---
title: 'Postupy: Přizpůsobení vazeb poskytovaných systémem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 7447830de81471c6d9e5b7812ec7a0ad1dbd2ccf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704703"
---
# <a name="how-to-customize-a-system-provided-binding"></a>Postupy: Přizpůsobení vazeb poskytovaných systémem
Windows Communication Foundation (WCF) zahrnuje několik vazeb poskytovaných systémem, které vám umožní nakonfigurovat některé vlastnosti základní prvky vazby, ale ne všechny vlastnosti. Toto téma ukazuje, jak nastavit vlastnosti v prvcích vazbu k vytvoření vlastní vazby.  
  
 Další informace o tom, jak přímo vytvořit a nakonfigurovat elementů vazby bez použití vazeb poskytovaných systémem najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Další informace o vytváření a rozšiřování vlastní vazby, naleznete v tématu [rozšíření vazby](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
 Ve službě WCF všechny vazby jsou tvořené *elementů vazby*. Každý element vazby je odvozen od <xref:System.ServiceModel.Channels.BindingElement> třídy. Vazby poskytované systémem, jako <xref:System.ServiceModel.BasicHttpBinding> vytvořit a nakonfigurovat vlastní elementy vazby. V tomto tématu se dozvíte, jak zobrazit a změnit vlastnosti tyto elementy vazby, které nejsou vystaveny přímo u vazby; Konkrétně <xref:System.ServiceModel.BasicHttpBinding> třídy.  
  
 Vazby jednotlivé prvky jsou obsaženy v kolekci reprezentována <xref:System.ServiceModel.Channels.BindingElementCollection> třídy a jsou přidány v tomto pořadí: Tok transakcí, stabilní relace, zabezpečení, kompozitní duplexní, jednosměrný Stream zabezpečení, kódování zpráv a přenosu. Všimněte si, že jsou všechny prvky vazby uvedené nezbytné Každá vazba. Uživatelem definované vazby prvky mohou také objevit v této kolekci elementů vazby a musí být ve stejném pořadí, jak je uvedeno výše. Například uživatelem definované přenosu musí být poslední element objektu kolekce elementů vazby.  
  
 <xref:System.ServiceModel.BasicHttpBinding> Třída obsahuje tři prvky vazby:  
  
1.  Volitelné zabezpečení vazby prvku buď <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> třída používaná s přenos pomocí protokolu HTTP (zabezpečení na úrovni zpráv) nebo <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> třídy, který se používá při přenosové vrstvy poskytuje zabezpečení, přičemž přenos protokolu HTTPS se používá.  
  
2.  Kodéru zprávy povinný element, buď vazby <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> nebo <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.  
  
3.  Vyžaduje přenos vazby prvku buď <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, nebo <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
 V tomto příkladu jsme vytvořit instanci vazby, generovat *vlastní vazby* z něj, zkontrolujte elementů vazby ve vlastní vazby, a pokud je nalezen element vazby protokolu HTTP, nastavíme jeho `KeepAliveEnabled` vlastnost `false`. `KeepAliveEnabled` Vlastnost nezveřejňují přímo na `BasicHttpBinding`, takže jsme musíte vytvořit vlastní vazby a přejděte dolů element vazby, nastavte tuto vlastnost.  
  
### <a name="to-modify-a-system-provided-binding"></a>K úpravě vazeb poskytovaných systémem  
  
1.  Vytvoření instance <xref:System.ServiceModel.BasicHttpBinding> třídy a nastavte jeho režim zabezpečení na úrovni zprávy.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  Vytvoření vlastní vazby z vazby a vytvořit <xref:System.ServiceModel.Channels.BindingElementCollection> třídy z jedné z vlastních vazbu vlastnosti.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  Projít <xref:System.ServiceModel.Channels.BindingElementCollection> třídy, a zjistíte, když <xref:System.ServiceModel.Channels.HttpTransportBindingElement> třídy, nastavte jeho <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> vlastnost `false`.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)
