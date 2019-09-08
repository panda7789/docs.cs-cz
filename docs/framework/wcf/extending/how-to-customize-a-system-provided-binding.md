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
# <a name="how-to-customize-a-system-provided-binding"></a><span data-ttu-id="483c7-102">Postupy: Přizpůsobení vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="483c7-102">How to: Customize a System-Provided Binding</span></span>
<span data-ttu-id="483c7-103">Windows Communication Foundation (WCF) obsahuje několik systémových vazeb, které umožňují konfigurovat některé vlastnosti podkladových prvků vazby, ale ne všechny vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="483c7-103">Windows Communication Foundation (WCF) includes several system-provided bindings that allow you to configure some of the properties of the underlying binding elements, but not all of the properties.</span></span> <span data-ttu-id="483c7-104">Toto téma ukazuje, jak nastavit vlastnosti prvků vazby k vytvoření vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="483c7-104">This topic demonstrates how to set properties on the binding elements to create a custom binding.</span></span>  
  
 <span data-ttu-id="483c7-105">Další informace o tom, jak přímo vytvářet a konfigurovat prvky vazby bez použití vazeb poskytovaných systémem, najdete v tématu [Custom Bindings](custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="483c7-105">For more information about how to directly create and configure binding elements without using the system-provided bindings, see [Custom Bindings](custom-bindings.md).</span></span>  
  
 <span data-ttu-id="483c7-106">Další informace o vytváření a rozšiřování vlastních vazeb naleznete v tématu [Extending Bindings](extending-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="483c7-106">For more information about creating and extending custom bindings, see [Extending Bindings](extending-bindings.md).</span></span>  
  
 <span data-ttu-id="483c7-107">V WCF jsou všechny vazby tvořeny *prvky vazby*.</span><span class="sxs-lookup"><span data-stu-id="483c7-107">In WCF all bindings are made up of *binding elements*.</span></span> <span data-ttu-id="483c7-108">Každý prvek vazby je odvozen z <xref:System.ServiceModel.Channels.BindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="483c7-108">Each binding element derives from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="483c7-109">Uživatelsky poskytnuté vazby, jako <xref:System.ServiceModel.BasicHttpBinding> je vytváření a konfigurace vlastních prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="483c7-109">System-provided bindings such as <xref:System.ServiceModel.BasicHttpBinding> create and configure their own binding elements.</span></span> <span data-ttu-id="483c7-110">V tomto tématu se dozvíte, jak získat přístup k vlastnostem těchto elementů vazby a jak je změnit, které nejsou přímo vystaveny na vazbě. <xref:System.ServiceModel.BasicHttpBinding> konkrétně třída.</span><span class="sxs-lookup"><span data-stu-id="483c7-110">This topic shows you how to access and change the properties of these binding elements, which are not directly exposed on the binding; specifically, the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="483c7-111">Jednotlivé prvky vazby jsou obsaženy v kolekci reprezentované <xref:System.ServiceModel.Channels.BindingElementCollection> třídou a jsou přidány v tomto pořadí: Tok transakcí, spolehlivé relace, zabezpečení, kompozitní duplexní, jednosměrné, zabezpečení datového proudu, kódování zpráv a přenos.</span><span class="sxs-lookup"><span data-stu-id="483c7-111">The individual binding elements are contained in a collection represented by the <xref:System.ServiceModel.Channels.BindingElementCollection> class and are added in this order: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding, and Transport.</span></span> <span data-ttu-id="483c7-112">Všimněte si, že ne všechny uvedené prvky vazby jsou požadovány při každé vazbě.</span><span class="sxs-lookup"><span data-stu-id="483c7-112">Note that not all the binding elements listed are required in every binding.</span></span> <span data-ttu-id="483c7-113">Uživatelsky definované prvky vazby mohou být také zobrazeny v této kolekci elementů vazby a musí se nacházet ve stejném pořadí, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="483c7-113">User-defined binding elements can also appear in this binding element collection and must appear in the same order as previously described.</span></span> <span data-ttu-id="483c7-114">Například přenos definovaný uživatelem musí být posledním prvkem kolekce elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="483c7-114">For example, a user-defined transport must be the last element of the binding element collection.</span></span>  
  
 <span data-ttu-id="483c7-115"><xref:System.ServiceModel.BasicHttpBinding> Třída obsahuje tři prvky vazby:</span><span class="sxs-lookup"><span data-stu-id="483c7-115">The <xref:System.ServiceModel.BasicHttpBinding> class contains three binding elements:</span></span>  
  
1. <span data-ttu-id="483c7-116">Volitelný prvek vazby zabezpečení, buď <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> Třída použitá s přenosem http (zabezpečení na úrovni zprávy), <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> nebo třída, která se používá, když přenosová vrstva poskytuje zabezpečení, v takovém případě se použije přenos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="483c7-116">An optional security binding element, either the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> class used with the HTTP transport (message level security) or the <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> class, which is used when the transport layer provides security, in which case the HTTPS transport is used.</span></span>  
  
2. <span data-ttu-id="483c7-117">Požadovaný prvek vazby kodéru zprávy buď <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> nebo. <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement></span><span class="sxs-lookup"><span data-stu-id="483c7-117">A required message encoder binding element, either <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> or <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span></span>  
  
3. <span data-ttu-id="483c7-118">Požadovaný prvek vazby přenosu, buď <xref:System.ServiceModel.Channels.HttpTransportBindingElement>nebo. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="483c7-118">A required transport binding element, either <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, or <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
 <span data-ttu-id="483c7-119">V tomto příkladu vytvoříme instanci vazby, vygenerujeme z ní *vlastní vazbu* , prověříme prvky vazby ve vlastní vazbě a když nalezneme element vazby HTTP, nastavíme `KeepAliveEnabled` vlastnost na. `false`</span><span class="sxs-lookup"><span data-stu-id="483c7-119">In this example we create an instance of the binding, generate a *custom binding* from it, examine the binding elements in the custom binding, and when we find the HTTP binding element, we set its `KeepAliveEnabled` property to `false`.</span></span> <span data-ttu-id="483c7-120">Vlastnost není přímo `BasicHttpBinding`k dispozici, takže je nutné vytvořit vlastní vazbu pro přechod k elementu vazby a nastavit tuto vlastnost. `KeepAliveEnabled`</span><span class="sxs-lookup"><span data-stu-id="483c7-120">The `KeepAliveEnabled` property is not exposed directly on the `BasicHttpBinding`, so we must create a custom binding to navigate down to the binding element and set this property.</span></span>  
  
### <a name="to-modify-a-system-provided-binding"></a><span data-ttu-id="483c7-121">Úprava vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="483c7-121">To modify a system-provided binding</span></span>  
  
1. <span data-ttu-id="483c7-122">Vytvořte instanci <xref:System.ServiceModel.BasicHttpBinding> třídy a nastavte její režim zabezpečení na úroveň zprávy.</span><span class="sxs-lookup"><span data-stu-id="483c7-122">Create an instance of the <xref:System.ServiceModel.BasicHttpBinding> class and set its security mode to message-level.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. <span data-ttu-id="483c7-123">Vytvořte vlastní vazbu z vazby a vytvořte <xref:System.ServiceModel.Channels.BindingElementCollection> třídu z jedné z vlastností vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="483c7-123">Create a custom binding from the binding and create a <xref:System.ServiceModel.Channels.BindingElementCollection> class from one of the custom binding's properties.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. <span data-ttu-id="483c7-124">Projděte <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> třídu a po nalezení třídy nastavte její vlastnost na `false`. <xref:System.ServiceModel.Channels.BindingElementCollection></span><span class="sxs-lookup"><span data-stu-id="483c7-124">Loop through the <xref:System.ServiceModel.Channels.BindingElementCollection> class, and when you find the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> class, set its <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property to `false`.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="483c7-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="483c7-125">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="483c7-126">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="483c7-126">Custom Bindings</span></span>](custom-bindings.md)
