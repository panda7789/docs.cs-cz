---
title: 'Postupy: Přizpůsobení vazeb poskytovaných systémem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 6b92382b4a37168c33f9e97077ad292d27ea5bc3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797021"
---
# <a name="how-to-customize-a-system-provided-binding"></a>Postupy: Přizpůsobení vazeb poskytovaných systémem
Windows Communication Foundation (WCF) obsahuje několik systémových vazeb, které umožňují konfigurovat některé vlastnosti podkladových prvků vazby, ale ne všechny vlastnosti. Toto téma ukazuje, jak nastavit vlastnosti prvků vazby k vytvoření vlastní vazby.  
  
 Další informace o tom, jak přímo vytvářet a konfigurovat prvky vazby bez použití vazeb poskytovaných systémem, najdete v tématu [Custom Bindings](custom-bindings.md).  
  
 Další informace o vytváření a rozšiřování vlastních vazeb naleznete v tématu [Extending Bindings](extending-bindings.md).  
  
 V WCF jsou všechny vazby tvořeny *prvky vazby*. Každý prvek vazby je odvozen z <xref:System.ServiceModel.Channels.BindingElement> třídy. Uživatelsky poskytnuté vazby, jako <xref:System.ServiceModel.BasicHttpBinding> je vytváření a konfigurace vlastních prvků vazby. V tomto tématu se dozvíte, jak získat přístup k vlastnostem těchto elementů vazby a jak je změnit, které nejsou přímo vystaveny na vazbě. <xref:System.ServiceModel.BasicHttpBinding> konkrétně třída.  
  
 Jednotlivé prvky vazby jsou obsaženy v kolekci reprezentované <xref:System.ServiceModel.Channels.BindingElementCollection> třídou a jsou přidány v tomto pořadí: Tok transakcí, spolehlivé relace, zabezpečení, kompozitní duplexní, jednosměrné, zabezpečení datového proudu, kódování zpráv a přenos. Všimněte si, že ne všechny uvedené prvky vazby jsou požadovány při každé vazbě. Uživatelsky definované prvky vazby mohou být také zobrazeny v této kolekci elementů vazby a musí se nacházet ve stejném pořadí, jak je popsáno výše. Například přenos definovaný uživatelem musí být posledním prvkem kolekce elementů vazby.  
  
 <xref:System.ServiceModel.BasicHttpBinding> Třída obsahuje tři prvky vazby:  
  
1. Volitelný prvek vazby zabezpečení, buď <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> Třída použitá s přenosem http (zabezpečení na úrovni zprávy), <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> nebo třída, která se používá, když přenosová vrstva poskytuje zabezpečení, v takovém případě se použije přenos HTTPS.  
  
2. Požadovaný prvek vazby kodéru zprávy buď <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> nebo. <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
3. Požadovaný prvek vazby přenosu, buď <xref:System.ServiceModel.Channels.HttpTransportBindingElement>nebo. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 V tomto příkladu vytvoříme instanci vazby, vygenerujeme z ní *vlastní vazbu* , prověříme prvky vazby ve vlastní vazbě a když nalezneme element vazby HTTP, nastavíme `KeepAliveEnabled` vlastnost na. `false` Vlastnost není přímo `BasicHttpBinding`k dispozici, takže je nutné vytvořit vlastní vazbu pro přechod k elementu vazby a nastavit tuto vlastnost. `KeepAliveEnabled`  
  
### <a name="to-modify-a-system-provided-binding"></a>Úprava vazby poskytované systémem  
  
1. Vytvořte instanci <xref:System.ServiceModel.BasicHttpBinding> třídy a nastavte její režim zabezpečení na úroveň zprávy.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. Vytvořte vlastní vazbu z vazby a vytvořte <xref:System.ServiceModel.Channels.BindingElementCollection> třídu z jedné z vlastností vlastní vazby.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. Projděte <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> třídu a po nalezení třídy nastavte její vlastnost na `false`. <xref:System.ServiceModel.Channels.BindingElementCollection>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vlastní vazby](custom-bindings.md)
