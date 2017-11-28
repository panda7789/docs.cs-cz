---
title: "Postupy: vystavení informačního kanálu jako Atom a RSS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 66b8ee21159d2900972a9cd8b42a9d26eefb8e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="a672d-102">Postupy: vystavení informačního kanálu jako Atom a RSS</span><span class="sxs-lookup"><span data-stu-id="a672d-102">How to: Expose a Feed as Both Atom and RSS</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="a672d-103">Umožňuje vytvořit službu, která zveřejňuje syndikace informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="a672d-103"> allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="a672d-104">Toto téma popisuje postup vytvoření syndikace služby, která zveřejňuje syndikace kanálu pomocí RSS 2.0 a Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="a672d-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="a672d-105">Tato služba zpřístupní jeden koncový bod, který může vrátit buď syndikace formátu.</span><span class="sxs-lookup"><span data-stu-id="a672d-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="a672d-106">Pro zjednodušení službu používanou v této ukázce je sám sebou hostované.</span><span class="sxs-lookup"><span data-stu-id="a672d-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="a672d-107">V produkčním prostředí by se v rámci služby IIS nebo WAS hostované služby tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="a672d-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a672d-108">různými [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hostování možnosti, najdete v části [hostitelský](../../../../docs/framework/wcf/feature-details/hosting.md).</span><span class="sxs-lookup"><span data-stu-id="a672d-108"> the different [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting options, see [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="a672d-109">Vytvoření služby základní syndikace</span><span class="sxs-lookup"><span data-stu-id="a672d-109">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="a672d-110">Definování kontraktu služby pomocí rozhraní označené jako <xref:System.ServiceModel.Web.WebGetAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="a672d-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="a672d-111">Každé operace, který je zveřejněný jako syndikace kanálu vrátí <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> objektu.</span><span class="sxs-lookup"><span data-stu-id="a672d-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="a672d-112">Poznámka: parametry <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a672d-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="a672d-113">`UriTemplate`Určuje adresu URL použije k vyvolání operace této služby.</span><span class="sxs-lookup"><span data-stu-id="a672d-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="a672d-114">Řetězec pro tento parametr obsahuje literály a proměnnou v závorkách ({*formát*}).</span><span class="sxs-lookup"><span data-stu-id="a672d-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="a672d-115">Tato proměnná odpovídá operace služby `format` parametr.</span><span class="sxs-lookup"><span data-stu-id="a672d-115">This variable corresponds to the service operation's `format` parameter.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="a672d-116"> <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="a672d-116"> <xref:System.UriTemplate>.</span></span> <span data-ttu-id="a672d-117">`BodyStyle`ovlivňuje, jak se zapisují zprávy, které tuto operaci služby odesílá a přijímá.</span><span class="sxs-lookup"><span data-stu-id="a672d-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="a672d-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Určuje, že data odesílaná do a z této operace služby nejsou zabalené službou infrastruktury definované elementů XML.</span><span class="sxs-lookup"><span data-stu-id="a672d-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="a672d-119"> <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="a672d-119"> <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="a672d-120">Použití <xref:System.ServiceModel.ServiceKnownTypeAttribute> určit typy, které jsou vráceny operacemi služby v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a672d-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2.  <span data-ttu-id="a672d-121">Implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="a672d-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  <span data-ttu-id="a672d-122">Vytvoření <xref:System.ServiceModel.Syndication.SyndicationFeed> objektu a přidejte vytváření, kategorie a popis.</span><span class="sxs-lookup"><span data-stu-id="a672d-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  <span data-ttu-id="a672d-123">Vytvořit několik <xref:System.ServiceModel.Syndication.SyndicationItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="a672d-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  <span data-ttu-id="a672d-124">Přidat <xref:System.ServiceModel.Syndication.SyndicationItem> objekty k informačnímu kanálu.</span><span class="sxs-lookup"><span data-stu-id="a672d-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  <span data-ttu-id="a672d-125">Použijte parametr formát vrátit požadovaný formát.</span><span class="sxs-lookup"><span data-stu-id="a672d-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="a672d-126">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="a672d-126">To host the service</span></span>  
  
1.  <span data-ttu-id="a672d-127">Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu.</span><span class="sxs-lookup"><span data-stu-id="a672d-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="a672d-128"><xref:System.ServiceModel.Web.WebServiceHost> Třída automaticky přidá koncový bod na základní adresa služby, pokud v konfiguraci nebo kód byl zadán jeden.</span><span class="sxs-lookup"><span data-stu-id="a672d-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="a672d-129">V této ukázce nejsou zadány žádné koncové body, je vystaven výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a672d-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  <span data-ttu-id="a672d-130">Otevření hostitele služby, načtěte informačního kanálu ze služby, zobrazit informační kanál a počkejte uživateli stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="a672d-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="a672d-131">K volání GetBlog s HTTP GET</span><span class="sxs-lookup"><span data-stu-id="a672d-131">To call GetBlog with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="a672d-132">Otevřete Internet Explorer, zadejte následující adresu URL a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="a672d-132">Open Internet Explorer, type the following URL, and press ENTER.</span></span> <span data-ttu-id="a672d-133">http://localhost: 8000/BlogService/GetBlog</span><span class="sxs-lookup"><span data-stu-id="a672d-133">http://localhost:8000/BlogService/GetBlog</span></span>  
  
     <span data-ttu-id="a672d-134">Adresa URL obsahuje základní adresa služby (http://localhost: 8000/BlogService), relativní adresa koncového bodu a volat operace služby.</span><span class="sxs-lookup"><span data-stu-id="a672d-134">The URL contains the base address of the service (http://localhost:8000/BlogService), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="a672d-135">GetBlog() volat z kódu</span><span class="sxs-lookup"><span data-stu-id="a672d-135">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="a672d-136">Vytvoření <xref:System.Xml.XmlReader> s základní adresu a při volání metody.</span><span class="sxs-lookup"><span data-stu-id="a672d-136">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="a672d-137">Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> předávání v případě metody <xref:System.Xml.XmlReader> jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="a672d-137">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="a672d-138">To vyvolá operaci služby a naplní novou <xref:System.ServiceModel.Syndication.SyndicationFeed> k formátování vrácená z operace služby.</span><span class="sxs-lookup"><span data-stu-id="a672d-138">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="a672d-139">Přístup k objekt informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="a672d-139">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="a672d-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="a672d-140">Example</span></span>  
 <span data-ttu-id="a672d-141">Zde je úplný výpis pro tento příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="a672d-141">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a672d-142">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a672d-142">Compiling the Code</span></span>  
 <span data-ttu-id="a672d-143">Při kompilování předchozí kód, odkazuje System.ServiceModel.dll a System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="a672d-143">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a672d-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="a672d-144">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
