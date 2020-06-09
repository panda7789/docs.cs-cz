---
title: 'Postupy: Vytvoření základního kanálu RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: 872fe325a6705e79d026cd7f6e1f7cfef5145307
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599019"
---
# <a name="how-to-create-a-basic-rss-feed"></a><span data-ttu-id="94490-102">Postupy: Vytvoření základního kanálu RSS</span><span class="sxs-lookup"><span data-stu-id="94490-102">How to: Create a Basic RSS Feed</span></span>
<span data-ttu-id="94490-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje kanál syndikace.</span><span class="sxs-lookup"><span data-stu-id="94490-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="94490-104">Toto téma popisuje, jak vytvořit službu syndikace, která zveřejňuje kanál syndikace RSS.</span><span class="sxs-lookup"><span data-stu-id="94490-104">This topic discusses how to create a syndication service that exposes an RSS syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="94490-105">Vytvoření služby syndikace na úrovni Basic</span><span class="sxs-lookup"><span data-stu-id="94490-105">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="94490-106">Definujte kontrakt služby pomocí rozhraní označeného <xref:System.ServiceModel.Web.WebGetAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="94490-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="94490-107">Každá operace, která je vystavena jako syndikační kanál, by měla vracet <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> objekt.</span><span class="sxs-lookup"><span data-stu-id="94490-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> object.</span></span>  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="94490-108">Všechny operace služby, které používají <xref:System.ServiceModel.Web.WebGetAttribute> atribut, jsou namapovány na požadavky HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="94490-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> attribute are mapped to HTTP GET requests.</span></span> <span data-ttu-id="94490-109">K namapování operace na jinou metodu HTTP použijte <xref:System.ServiceModel.Web.WebInvokeAttribute> místo nich.</span><span class="sxs-lookup"><span data-stu-id="94490-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="94490-110">Další informace naleznete v tématu [How to: Create a Basic WCF web http Service](how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="94490-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2. <span data-ttu-id="94490-111">Implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="94490-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3. <span data-ttu-id="94490-112">Vytvořte <xref:System.ServiceModel.Syndication.SyndicationFeed> objekt a přidejte jeho autora, kategorii a popis.</span><span class="sxs-lookup"><span data-stu-id="94490-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4. <span data-ttu-id="94490-113">Vytvořte několik <xref:System.ServiceModel.Syndication.SyndicationItem> objektů.</span><span class="sxs-lookup"><span data-stu-id="94490-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5. <span data-ttu-id="94490-114">Přidejte <xref:System.ServiceModel.Syndication.SyndicationItem> do informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="94490-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> to the feed.</span></span>  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6. <span data-ttu-id="94490-115">Vrácení informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="94490-115">Return the feed.</span></span>  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a><span data-ttu-id="94490-116">Hostování služby</span><span class="sxs-lookup"><span data-stu-id="94490-116">To host a service</span></span>  
  
1. <span data-ttu-id="94490-117">Vytvořte <xref:System.ServiceModel.Web.WebServiceHost> objekt.</span><span class="sxs-lookup"><span data-stu-id="94490-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2. <span data-ttu-id="94490-118">Otevřete hostitele služby a počkejte, dokud uživatel nestiskne klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="94490-118">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="94490-119">Volání metody getblog () pomocí protokolu HTTP GET</span><span class="sxs-lookup"><span data-stu-id="94490-119">To call GetBlog() with an HTTP GET</span></span>  
  
1. <span data-ttu-id="94490-120">Otevřete Internet Explorer, zadejte následující adresu URL a stiskněte klávesu ENTER: `http://localhost:8000/BlogService/GetBlog` .</span><span class="sxs-lookup"><span data-stu-id="94490-120">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span> <span data-ttu-id="94490-121">Adresa URL obsahuje základní adresu služby ( `http://localhost:8000/BlogService` ), relativní adresu koncového bodu a volanou operaci služby.</span><span class="sxs-lookup"><span data-stu-id="94490-121">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="94490-122">Volání metody getblog () z kódu</span><span class="sxs-lookup"><span data-stu-id="94490-122">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="94490-123">Vytvořte <xref:System.Xml.XmlReader> se základní adresou a metodou, kterou voláte.</span><span class="sxs-lookup"><span data-stu-id="94490-123">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="94490-124">Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metodu a předejte ji <xref:System.Xml.XmlReader> právě vytvořenou.</span><span class="sxs-lookup"><span data-stu-id="94490-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="94490-125">Tím se vyvolá operace služby a naplní se <xref:System.ServiceModel.Syndication.SyndicationFeed> formátovací modul vrácený funkcí operace služby.</span><span class="sxs-lookup"><span data-stu-id="94490-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="94490-126">Přístup k objektu informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="94490-126">Access the feed object.</span></span>  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="94490-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="94490-127">Example</span></span>  
 <span data-ttu-id="94490-128">Následuje úplný výpis kódu pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="94490-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94490-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="94490-129">Compiling the Code</span></span>  
 <span data-ttu-id="94490-130">Při kompilování předchozího kódu, odkazuje na System. ServiceModel. dll a System. ServiceModel. Web. dll.</span><span class="sxs-lookup"><span data-stu-id="94490-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94490-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="94490-131">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
