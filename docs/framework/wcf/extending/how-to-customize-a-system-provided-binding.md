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
# <a name="how-to-customize-a-system-provided-binding"></a><span data-ttu-id="7b928-102">Postupy: přizpůsobení vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="7b928-102">How to: Customize a System-Provided Binding</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="7b928-103"> zahrnuje několik vazeb poskytovaných systémem, které vám umožní nakonfigurovat některé vlastnosti základní prvky vazby, ale ne všechny vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7b928-103"> includes several system-provided bindings that allow you to configure some of the properties of the underlying binding elements, but not all of the properties.</span></span> <span data-ttu-id="7b928-104">Toto téma ukazuje, jak nastavit vlastnosti u elementů vazby k vytvoření vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="7b928-104">This topic demonstrates how to set properties on the binding elements to create a custom binding.</span></span>  
  
 <span data-ttu-id="7b928-105">Další informace o tom, jak přímo vytvořit a nakonfigurovat prvky vazeb bez použití vazby poskytované systémem najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="7b928-105">For more information about how to directly create and configure binding elements without using the system-provided bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
 <span data-ttu-id="7b928-106">Další informace o vytváření a rozšíření vlastních vazeb najdete v tématu [rozšíření vazby](../../../../docs/framework/wcf/extending/extending-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="7b928-106">For more information about creating and extending custom bindings, see [Extending Bindings](../../../../docs/framework/wcf/extending/extending-bindings.md).</span></span>  
  
 <span data-ttu-id="7b928-107">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] všechny vazby jsou tvořeny *elementů vazby*.</span><span class="sxs-lookup"><span data-stu-id="7b928-107">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] all bindings are made up of *binding elements*.</span></span> <span data-ttu-id="7b928-108">Každý prvek vazba je odvozena z <xref:System.ServiceModel.Channels.BindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="7b928-108">Each binding element derives from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="7b928-109">Vazby poskytované systémem, jako <xref:System.ServiceModel.BasicHttpBinding> vytvořit a nakonfigurovat vlastní prvky vazeb.</span><span class="sxs-lookup"><span data-stu-id="7b928-109">System-provided bindings such as <xref:System.ServiceModel.BasicHttpBinding> create and configure their own binding elements.</span></span> <span data-ttu-id="7b928-110">Toto téma ukazuje, jak získávat přístup a měnit vlastnosti z těchto elementů vazby, které nejsou přímo přístupné na vazby; Konkrétně <xref:System.ServiceModel.BasicHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="7b928-110">This topic shows you how to access and change the properties of these binding elements, which are not directly exposed on the binding; specifically, the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="7b928-111">Prvky jednotlivé vazby jsou obsaženy v kolekci reprezentována <xref:System.ServiceModel.Channels.BindingElementCollection> třídy a přidají se v tomto pořadí: toku transakcí, spolehlivé relace, zabezpečení, složené duplexní, jednosměrné, zabezpečení datového proudu, kódování zpráv a přenosu.</span><span class="sxs-lookup"><span data-stu-id="7b928-111">The individual binding elements are contained in a collection represented by the <xref:System.ServiceModel.Channels.BindingElementCollection> class and are added in this order: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding, and Transport.</span></span> <span data-ttu-id="7b928-112">Všimněte si, že ne všechny prvky vazby uvedené jsou potřeba v každé vazby.</span><span class="sxs-lookup"><span data-stu-id="7b928-112">Note that not all the binding elements listed are required in every binding.</span></span> <span data-ttu-id="7b928-113">Uživatelem definované vazby elementy může zobrazit i v této kolekci elementů vazby a musí se nacházet ve stejném pořadí jako výše popsané.</span><span class="sxs-lookup"><span data-stu-id="7b928-113">User-defined binding elements can also appear in this binding element collection and must appear in the same order as previously described.</span></span> <span data-ttu-id="7b928-114">Uživatelem definované přenos například musí být posledním prvkem kolekce elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="7b928-114">For example, a user-defined transport must be the last element of the binding element collection.</span></span>  
  
 <span data-ttu-id="7b928-115"><xref:System.ServiceModel.BasicHttpBinding> Třída obsahuje tři prvky vazeb:</span><span class="sxs-lookup"><span data-stu-id="7b928-115">The <xref:System.ServiceModel.BasicHttpBinding> class contains three binding elements:</span></span>  
  
1.  <span data-ttu-id="7b928-116">Zabezpečení služby volitelné vazby elementu, buď <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> třída používaná s HTTP přenosu (úrovně zabezpečení zpráv) nebo <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> se používá třída, která se používá při přenosové vrstvy poskytuje zabezpečení, která případ přenos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7b928-116">An optional security binding element, either the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> class used with the HTTP transport (message level security) or the <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> class, which is used when the transport layer provides security, in which case the HTTPS transport is used.</span></span>  
  
2.  <span data-ttu-id="7b928-117">Kodéru zprávy požadované vazby elementu, buď <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> nebo <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="7b928-117">A required message encoder binding element, either <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> or <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span></span>  
  
3.  <span data-ttu-id="7b928-118">Vyžaduje přenos buď vazby elementu <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, nebo <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="7b928-118">A required transport binding element, either <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, or <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
 <span data-ttu-id="7b928-119">V tomto příkladu jsme vytvoření instance vazby, vygenerujte *vlastní vazby* z něj, zkontrolujte elementů vazby ve vlastní vazby, a pokud je nalezen element vazby HTTP, nastaví její `KeepAliveEnabled` vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="7b928-119">In this example we create an instance of the binding, generate a *custom binding* from it, examine the binding elements in the custom binding, and when we find the HTTP binding element, we set its `KeepAliveEnabled` property to `false`.</span></span> <span data-ttu-id="7b928-120">`KeepAliveEnabled` Vlastnost není k dispozici přímo na `BasicHttpBinding`, takže jsme musí vytvořit vlastní vazby přejděte dolů prvku vazby a nastavte tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7b928-120">The `KeepAliveEnabled` property is not exposed directly on the `BasicHttpBinding`, so we must create a custom binding to navigate down to the binding element and set this property.</span></span>  
  
### <a name="to-modify-a-system-provided-binding"></a><span data-ttu-id="7b928-121">Chcete-li upravit vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="7b928-121">To modify a system-provided binding</span></span>  
  
1.  <span data-ttu-id="7b928-122">Vytvoření instance <xref:System.ServiceModel.BasicHttpBinding> třídy a nastavte režim zabezpečení na úrovni zpráv.</span><span class="sxs-lookup"><span data-stu-id="7b928-122">Create an instance of the <xref:System.ServiceModel.BasicHttpBinding> class and set its security mode to message-level.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  <span data-ttu-id="7b928-123">Vytvoření vlastní vazby z vazby a vytvořte <xref:System.ServiceModel.Channels.BindingElementCollection> třídy z jedné z vlastností vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="7b928-123">Create a custom binding from the binding and create a <xref:System.ServiceModel.Channels.BindingElementCollection> class from one of the custom binding's properties.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  <span data-ttu-id="7b928-124">Procházení <xref:System.ServiceModel.Channels.BindingElementCollection> třída, a při vyhledání <xref:System.ServiceModel.Channels.HttpTransportBindingElement> třídy, nastavte jeho <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="7b928-124">Loop through the <xref:System.ServiceModel.Channels.BindingElementCollection> class, and when you find the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> class, set its <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property to `false`.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="7b928-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b928-125">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="7b928-126">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="7b928-126">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
