---
title: 'Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 43ad8ae0b12b07e2d0abe3e208f6d1ccdb2ec77d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681167"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="855f0-102">Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS</span><span class="sxs-lookup"><span data-stu-id="855f0-102">How to: Expose a Feed as Both Atom and RSS</span></span>
<span data-ttu-id="855f0-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje informačního kanálu syndikace.</span><span class="sxs-lookup"><span data-stu-id="855f0-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="855f0-104">Toto téma popisuje, jak vytvořit služby syndikace, který zpřístupňuje kanálem syndikace Atom 1.0 i RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="855f0-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="855f0-105">Tato služba poskytuje jeden koncový bod, který může vrátit buď souhrnný formát, který.</span><span class="sxs-lookup"><span data-stu-id="855f0-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="855f0-106">Pro zjednodušení služby používané v tomto příkladu je nezávislý hostované.</span><span class="sxs-lookup"><span data-stu-id="855f0-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="855f0-107">V produkčním prostředí by být hostované služby tohoto typu v rámci služby IIS nebo WAS.</span><span class="sxs-lookup"><span data-stu-id="855f0-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="855f0-108">Další informace o různých WCF možnosti hostování naleznete v tématu [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).</span><span class="sxs-lookup"><span data-stu-id="855f0-108">For more information about the different WCF hosting options, see [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="855f0-109">Chcete-li vytvořit základní syndikační služby</span><span class="sxs-lookup"><span data-stu-id="855f0-109">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="855f0-110">Definování kontraktu služby pomocí rozhraní označené <xref:System.ServiceModel.Web.WebGetAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="855f0-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="855f0-111">Každá operace, která je vystavena jako kanálu syndikace vrátí <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> objektu.</span><span class="sxs-lookup"><span data-stu-id="855f0-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="855f0-112">Poznámka: parametry <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="855f0-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="855f0-113">`UriTemplate` Určuje adresu URL použít k vyvolání operace této služby.</span><span class="sxs-lookup"><span data-stu-id="855f0-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="855f0-114">Řetězec pro tento parametr obsahuje literály a proměnné ve složených závorkách ({*formátu*}).</span><span class="sxs-lookup"><span data-stu-id="855f0-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="855f0-115">Tato proměnná odpovídá operaci služby `format` parametru.</span><span class="sxs-lookup"><span data-stu-id="855f0-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="855f0-116">Další informace naleznete v tématu <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="855f0-116">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="855f0-117">`BodyStyle` ovlivňuje, jak se zapisují zprávy, které tuto operaci služba odesílá a přijímá.</span><span class="sxs-lookup"><span data-stu-id="855f0-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="855f0-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> Určuje, že data odesílaná do a z této operace služby nejsou zabalené službou infrastruktury definované elementy XML.</span><span class="sxs-lookup"><span data-stu-id="855f0-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="855f0-119">Další informace naleznete v tématu <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="855f0-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="855f0-120">Použití <xref:System.ServiceModel.ServiceKnownTypeAttribute> určit typy, které jsou vráceny pomocí operací služby v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="855f0-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2.  <span data-ttu-id="855f0-121">Implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="855f0-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  <span data-ttu-id="855f0-122">Vytvoření <xref:System.ServiceModel.Syndication.SyndicationFeed> objektu a přidejte Autor, kategorie a popis.</span><span class="sxs-lookup"><span data-stu-id="855f0-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  <span data-ttu-id="855f0-123">Vytvoření několika <xref:System.ServiceModel.Syndication.SyndicationItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="855f0-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  <span data-ttu-id="855f0-124">Přidat <xref:System.ServiceModel.Syndication.SyndicationItem> objekty do informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="855f0-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  <span data-ttu-id="855f0-125">Pomocí parametru formátu vrátit požadovanému formátu.</span><span class="sxs-lookup"><span data-stu-id="855f0-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="855f0-126">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="855f0-126">To host the service</span></span>  
  
1.  <span data-ttu-id="855f0-127">Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu.</span><span class="sxs-lookup"><span data-stu-id="855f0-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="855f0-128"><xref:System.ServiceModel.Web.WebServiceHost> Třída automaticky přidá koncový bod na základní adrese služby, pokud je zadaná v kódu nebo konfigurace.</span><span class="sxs-lookup"><span data-stu-id="855f0-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="855f0-129">V této ukázce jsou určeny žádné koncové body tak výchozí koncový bod je přístupný.</span><span class="sxs-lookup"><span data-stu-id="855f0-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  <span data-ttu-id="855f0-130">Otevření hostitele služby, načtení informačního kanálu ze služby, zobrazit informační kanál a čekat, uživatel stisknout klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="855f0-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="855f0-131">Chcete-li volat GetBlog s HTTP GET</span><span class="sxs-lookup"><span data-stu-id="855f0-131">To call GetBlog with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="855f0-132">Spusťte aplikaci Internet Explorer a zadejte následující adresu URL, stiskněte klávesu ENTER: `http://localhost:8000/BlogService/GetBlog`.</span><span class="sxs-lookup"><span data-stu-id="855f0-132">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="855f0-133">Adresa URL obsahuje základní adresa služby (`http://localhost:8000/BlogService`), relativní adresu koncového bodu a operace služby, která volá.</span><span class="sxs-lookup"><span data-stu-id="855f0-133">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="855f0-134">GetBlog() volat z kódu</span><span class="sxs-lookup"><span data-stu-id="855f0-134">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="855f0-135">Vytvoření <xref:System.Xml.XmlReader> k základní adrese a metodu voláte.</span><span class="sxs-lookup"><span data-stu-id="855f0-135">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="855f0-136">Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metodu <xref:System.Xml.XmlReader> jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="855f0-136">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="855f0-137">To vyvolá operaci služby a naplní nový <xref:System.ServiceModel.Syndication.SyndicationFeed> formátování vrácená z operace služby.</span><span class="sxs-lookup"><span data-stu-id="855f0-137">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="855f0-138">Přístup k objekt informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="855f0-138">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="855f0-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="855f0-139">Example</span></span>  
 <span data-ttu-id="855f0-140">Následuje úplný výpis v tomto příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="855f0-140">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="855f0-141">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="855f0-141">Compiling the Code</span></span>  
 <span data-ttu-id="855f0-142">Při kompilaci předchozí kód, odkazovat System.ServiceModel.dll a System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="855f0-142">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="855f0-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="855f0-143">See also</span></span>
- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
