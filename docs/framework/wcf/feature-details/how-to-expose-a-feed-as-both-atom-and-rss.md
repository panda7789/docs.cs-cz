---
title: 'Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: e4ce1fa7b494c2317a1bddc57ee6b150c84b9a96
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593143"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="de9b9-102">Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS</span><span class="sxs-lookup"><span data-stu-id="de9b9-102">How to: Expose a Feed as Both Atom and RSS</span></span>
<span data-ttu-id="de9b9-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje kanál syndikace.</span><span class="sxs-lookup"><span data-stu-id="de9b9-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="de9b9-104">Toto téma popisuje, jak vytvořit službu syndikace, která zveřejňuje kanál syndikace pomocí Atom 1,0 a RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="de9b9-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="de9b9-105">Tato služba zpřístupňuje jeden koncový bod, který může vracet buď formát syndikace.</span><span class="sxs-lookup"><span data-stu-id="de9b9-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="de9b9-106">Pro jednoduchost služby použité v této ukázce se jedná o samoobslužné hostování.</span><span class="sxs-lookup"><span data-stu-id="de9b9-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="de9b9-107">V produkčním prostředí by služba tohoto typu byla hostována službou IIS nebo WAS.</span><span class="sxs-lookup"><span data-stu-id="de9b9-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="de9b9-108">Další informace o různých možnostech hostování WCF naleznete v tématu [hosting](hosting.md).</span><span class="sxs-lookup"><span data-stu-id="de9b9-108">For more information about the different WCF hosting options, see [Hosting](hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="de9b9-109">Vytvoření služby syndikace na úrovni Basic</span><span class="sxs-lookup"><span data-stu-id="de9b9-109">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="de9b9-110">Definujte kontrakt služby pomocí rozhraní označeného <xref:System.ServiceModel.Web.WebGetAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="de9b9-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="de9b9-111">Každá operace, která je vystavena jako syndikační kanál, vrací <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> objekt.</span><span class="sxs-lookup"><span data-stu-id="de9b9-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="de9b9-112">Všimněte si parametrů pro <xref:System.ServiceModel.Web.WebGetAttribute> .</span><span class="sxs-lookup"><span data-stu-id="de9b9-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="de9b9-113">`UriTemplate`Určuje adresu URL, která se používá k vyvolání této operace služby.</span><span class="sxs-lookup"><span data-stu-id="de9b9-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="de9b9-114">Řetězec pro tento parametr obsahuje literály a proměnnou ve složených závorkách ({*Format*}).</span><span class="sxs-lookup"><span data-stu-id="de9b9-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="de9b9-115">Tato proměnná odpovídá parametru operace služby `format` .</span><span class="sxs-lookup"><span data-stu-id="de9b9-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="de9b9-116">Další informace naleznete v tématu <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="de9b9-116">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="de9b9-117">`BodyStyle`má vliv na zápis zpráv, které tato operace služby odesílá a přijímá.</span><span class="sxs-lookup"><span data-stu-id="de9b9-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="de9b9-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Určuje, že data odesílaná do a z této operace služby nejsou zabalena pomocí prvků XML definovaných v infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="de9b9-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="de9b9-119">Další informace naleznete v tématu <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="de9b9-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="de9b9-120">Použijte <xref:System.ServiceModel.ServiceKnownTypeAttribute> k určení typů, které jsou vráceny operacemi služby v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="de9b9-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2. <span data-ttu-id="de9b9-121">Implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="de9b9-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. <span data-ttu-id="de9b9-122">Vytvořte <xref:System.ServiceModel.Syndication.SyndicationFeed> objekt a přidejte jeho autora, kategorii a popis.</span><span class="sxs-lookup"><span data-stu-id="de9b9-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. <span data-ttu-id="de9b9-123">Vytvořte několik <xref:System.ServiceModel.Syndication.SyndicationItem> objektů.</span><span class="sxs-lookup"><span data-stu-id="de9b9-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <span data-ttu-id="de9b9-124">Přidejte <xref:System.ServiceModel.Syndication.SyndicationItem> objekty do informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="de9b9-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. <span data-ttu-id="de9b9-125">Pro vrácení požadovaného formátu použijte parametr format.</span><span class="sxs-lookup"><span data-stu-id="de9b9-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="de9b9-126">Hostování služby</span><span class="sxs-lookup"><span data-stu-id="de9b9-126">To host the service</span></span>  
  
1. <span data-ttu-id="de9b9-127">Vytvořte <xref:System.ServiceModel.Web.WebServiceHost> objekt.</span><span class="sxs-lookup"><span data-stu-id="de9b9-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="de9b9-128"><xref:System.ServiceModel.Web.WebServiceHost>Třída automaticky přidá koncový bod na základní adrese služby, není-li v kódu nebo konfiguraci zadána jedna.</span><span class="sxs-lookup"><span data-stu-id="de9b9-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="de9b9-129">V této ukázce nejsou zadány žádné koncové body, aby byl výchozí koncový bod vystaven.</span><span class="sxs-lookup"><span data-stu-id="de9b9-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. <span data-ttu-id="de9b9-130">Otevřete hostitele služby, načtěte kanál ze služby, zobrazte informační kanál a počkejte, než uživatel stiskne klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="de9b9-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="de9b9-131">Volání metody getblog s protokolem HTTP GET</span><span class="sxs-lookup"><span data-stu-id="de9b9-131">To call GetBlog with an HTTP GET</span></span>  
  
1. <span data-ttu-id="de9b9-132">Otevřete Internet Explorer, zadejte následující adresu URL a stiskněte klávesu ENTER: `http://localhost:8000/BlogService/GetBlog` .</span><span class="sxs-lookup"><span data-stu-id="de9b9-132">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="de9b9-133">Adresa URL obsahuje základní adresu služby ( `http://localhost:8000/BlogService` ), relativní adresu koncového bodu a volanou operaci služby.</span><span class="sxs-lookup"><span data-stu-id="de9b9-133">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="de9b9-134">Volání metody getblog () z kódu</span><span class="sxs-lookup"><span data-stu-id="de9b9-134">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="de9b9-135">Vytvořte <xref:System.Xml.XmlReader> se základní adresou a metodou, kterou voláte.</span><span class="sxs-lookup"><span data-stu-id="de9b9-135">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="de9b9-136">Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metodu a předejte ji <xref:System.Xml.XmlReader> právě vytvořenou.</span><span class="sxs-lookup"><span data-stu-id="de9b9-136">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="de9b9-137">Tím se vyvolá operace služby a naplní se <xref:System.ServiceModel.Syndication.SyndicationFeed> formátovací modul vrácený funkcí operace služby.</span><span class="sxs-lookup"><span data-stu-id="de9b9-137">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="de9b9-138">Přístup k objektu informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="de9b9-138">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="de9b9-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="de9b9-139">Example</span></span>  
 <span data-ttu-id="de9b9-140">Následuje úplný výpis kódu pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="de9b9-140">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de9b9-141">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="de9b9-141">Compiling the Code</span></span>  
 <span data-ttu-id="de9b9-142">Při kompilování předchozího kódu, odkazuje na System. ServiceModel. dll a System. ServiceModel. Web. dll.</span><span class="sxs-lookup"><span data-stu-id="de9b9-142">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de9b9-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="de9b9-143">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
