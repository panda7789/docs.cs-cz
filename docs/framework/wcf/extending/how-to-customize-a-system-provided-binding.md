---
title: 'Postupy: přizpůsobení vazby poskytované systémem'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1d70a4c4234047e7410ae4f631e48595a0859f37
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-customize-a-system-provided-binding"></a>Postupy: přizpůsobení vazby poskytované systémem
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zahrnuje několik vazeb poskytovaných systémem, které vám umožní nakonfigurovat některé vlastnosti základní prvky vazby, ale ne všechny vlastnosti. Toto téma ukazuje, jak nastavit vlastnosti u elementů vazby k vytvoření vlastní vazby.  
  
 Další informace o tom, jak přímo vytvořit a nakonfigurovat prvky vazeb bez použití vazby poskytované systémem najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Další informace o vytváření a rozšíření vlastních vazeb najdete v tématu [rozšíření vazby](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] všechny vazby jsou tvořeny *elementů vazby*. Každý prvek vazba je odvozena z <xref:System.ServiceModel.Channels.BindingElement> třídy. Vazby poskytované systémem, jako <xref:System.ServiceModel.BasicHttpBinding> vytvořit a nakonfigurovat vlastní prvky vazeb. Toto téma ukazuje, jak získávat přístup a měnit vlastnosti z těchto elementů vazby, které nejsou přímo přístupné na vazby; Konkrétně <xref:System.ServiceModel.BasicHttpBinding> třídy.  
  
 Prvky jednotlivé vazby jsou obsaženy v kolekci reprezentována <xref:System.ServiceModel.Channels.BindingElementCollection> třídy a přidají se v tomto pořadí: toku transakcí, spolehlivé relace, zabezpečení, složené duplexní, jednosměrné, zabezpečení datového proudu, kódování zpráv a přenosu. Všimněte si, že ne všechny prvky vazby uvedené jsou potřeba v každé vazby. Uživatelem definované vazby elementy může zobrazit i v této kolekci elementů vazby a musí se nacházet ve stejném pořadí jako výše popsané. Uživatelem definované přenos například musí být posledním prvkem kolekce elementů vazby.  
  
 <xref:System.ServiceModel.BasicHttpBinding> Třída obsahuje tři prvky vazeb:  
  
1.  Zabezpečení služby volitelné vazby elementu, buď <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> třída používaná s HTTP přenosu (úrovně zabezpečení zpráv) nebo <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> se používá třída, která se používá při přenosové vrstvy poskytuje zabezpečení, která případ přenos HTTPS.  
  
2.  Kodéru zprávy požadované vazby elementu, buď <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> nebo <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.  
  
3.  Vyžaduje přenos buď vazby elementu <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, nebo <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
 V tomto příkladu jsme vytvoření instance vazby, vygenerujte *vlastní vazby* z něj, zkontrolujte elementů vazby ve vlastní vazby, a pokud je nalezen element vazby HTTP, nastaví její `KeepAliveEnabled` vlastnost `false`. `KeepAliveEnabled` Vlastnost není k dispozici přímo na `BasicHttpBinding`, takže jsme musí vytvořit vlastní vazby přejděte dolů prvku vazby a nastavte tuto vlastnost.  
  
### <a name="to-modify-a-system-provided-binding"></a>Chcete-li upravit vazby poskytované systémem  
  
1.  Vytvoření instance <xref:System.ServiceModel.BasicHttpBinding> třídy a nastavte režim zabezpečení na úrovni zpráv.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  Vytvoření vlastní vazby z vazby a vytvořte <xref:System.ServiceModel.Channels.BindingElementCollection> třídy z jedné z vlastností vlastní vazby.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  Procházení <xref:System.ServiceModel.Channels.BindingElementCollection> třída, a při vyhledání <xref:System.ServiceModel.Channels.HttpTransportBindingElement> třídy, nastavte jeho <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> vlastnost `false`.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)
