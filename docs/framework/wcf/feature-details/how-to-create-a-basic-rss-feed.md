---
title: 'Postupy: Vytvoření základního kanálu RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: 5bab8b5a19f33f8dcfcc5a5f5d882309a4b1cc99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781443"
---
# <a name="how-to-create-a-basic-rss-feed"></a><span data-ttu-id="70823-102">Postupy: Vytvoření základního kanálu RSS</span><span class="sxs-lookup"><span data-stu-id="70823-102">How to: Create a Basic RSS Feed</span></span>
<span data-ttu-id="70823-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje informačního kanálu syndikace.</span><span class="sxs-lookup"><span data-stu-id="70823-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="70823-104">Toto téma popisuje, jak vytvořit služby syndikace, který zpřístupňuje informačního kanálu syndikace RSS.</span><span class="sxs-lookup"><span data-stu-id="70823-104">This topic discusses how to create a syndication service that exposes an RSS syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="70823-105">Chcete-li vytvořit základní syndikační služby</span><span class="sxs-lookup"><span data-stu-id="70823-105">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="70823-106">Definování kontraktu služby pomocí rozhraní označené <xref:System.ServiceModel.Web.WebGetAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="70823-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="70823-107">Každá operace, která je vystavena jako informační kanál syndikace by mělo vrátit <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> objektu.</span><span class="sxs-lookup"><span data-stu-id="70823-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> object.</span></span>  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="70823-108">Všechny operace služby, které se vztahují <xref:System.ServiceModel.Web.WebGetAttribute> atribut se mapují na požadavky HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="70823-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> attribute are mapped to HTTP GET requests.</span></span> <span data-ttu-id="70823-109">Chcete-li namapovat operace jinou metodu HTTP, použijte <xref:System.ServiceModel.Web.WebInvokeAttribute> místo.</span><span class="sxs-lookup"><span data-stu-id="70823-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="70823-110">Další informace najdete v tématu [jak: Vytvoření webové služby HTTP WCF základní](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="70823-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2. <span data-ttu-id="70823-111">Implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="70823-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3. <span data-ttu-id="70823-112">Vytvoření <xref:System.ServiceModel.Syndication.SyndicationFeed> objektu a přidejte Autor, kategorie a popis.</span><span class="sxs-lookup"><span data-stu-id="70823-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4. <span data-ttu-id="70823-113">Vytvoření několika <xref:System.ServiceModel.Syndication.SyndicationItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="70823-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5. <span data-ttu-id="70823-114">Přidat <xref:System.ServiceModel.Syndication.SyndicationItem> do informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="70823-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> to the feed.</span></span>  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6. <span data-ttu-id="70823-115">Vrátí informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="70823-115">Return the feed.</span></span>  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a><span data-ttu-id="70823-116">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="70823-116">To host a service</span></span>  
  
1. <span data-ttu-id="70823-117">Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu.</span><span class="sxs-lookup"><span data-stu-id="70823-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2. <span data-ttu-id="70823-118">Otevření hostitele služby a počkejte, až uživatel stiskne klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="70823-118">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="70823-119">Chcete-li volat GetBlog() s HTTP GET</span><span class="sxs-lookup"><span data-stu-id="70823-119">To call GetBlog() with an HTTP GET</span></span>  
  
1. <span data-ttu-id="70823-120">Spusťte aplikaci Internet Explorer a zadejte následující adresu URL, stiskněte klávesu ENTER: `http://localhost:8000/BlogService/GetBlog`.</span><span class="sxs-lookup"><span data-stu-id="70823-120">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span> <span data-ttu-id="70823-121">Adresa URL obsahuje základní adresa služby (`http://localhost:8000/BlogService`), relativní adresu koncového bodu a operace služby, která volá.</span><span class="sxs-lookup"><span data-stu-id="70823-121">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="70823-122">GetBlog() volat z kódu</span><span class="sxs-lookup"><span data-stu-id="70823-122">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="70823-123">Vytvoření <xref:System.Xml.XmlReader> k základní adrese a metodu voláte.</span><span class="sxs-lookup"><span data-stu-id="70823-123">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="70823-124">Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metodu <xref:System.Xml.XmlReader> jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="70823-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="70823-125">To vyvolá operaci služby a naplní nový <xref:System.ServiceModel.Syndication.SyndicationFeed> formátování vrácená z operace služby.</span><span class="sxs-lookup"><span data-stu-id="70823-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="70823-126">Přístup k objekt informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="70823-126">Access the feed object.</span></span>  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="70823-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="70823-127">Example</span></span>  
 <span data-ttu-id="70823-128">Následuje úplný výpis v tomto příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="70823-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="70823-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="70823-129">Compiling the Code</span></span>  
 <span data-ttu-id="70823-130">Při kompilaci předchozí kód, odkazovat System.ServiceModel.dll a System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="70823-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70823-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70823-131">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
