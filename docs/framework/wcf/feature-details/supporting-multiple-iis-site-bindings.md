---
title: Podpora víc vazeb webu IIS
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4b586b4d5c3c37355bf7b05a8a0227565a5b5e5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="supporting-multiple-iis-site-bindings"></a><span data-ttu-id="56d2c-102">Podpora víc vazeb webu IIS</span><span class="sxs-lookup"><span data-stu-id="56d2c-102">Supporting Multiple IIS Site Bindings</span></span>
<span data-ttu-id="56d2c-103">Při hostování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby v části Internetové informační služby (IIS) 7.0, můžete zadat více základní adresy, která používá stejný protokol ve stejné lokalitě.</span><span class="sxs-lookup"><span data-stu-id="56d2c-103">When hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under Internet Information Services (IIS) 7.0, you may want to provide multiple base addresses that use the same protocol on the same site.</span></span> <span data-ttu-id="56d2c-104">To umožňuje stejnou službu reagovat na několika různých identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="56d2c-104">This allows the same service to respond to a number of different URIs.</span></span> <span data-ttu-id="56d2c-105">To je užitečné, když chcete hostovat službu, která naslouchá na http://www.contoso.com a http://contoso.com. Je také užitečné k vytvoření služby, který má bázové adresy pro interní uživatele a samostatné základní adresa pro externí uživatele.</span><span class="sxs-lookup"><span data-stu-id="56d2c-105">This is useful when you want to host a service that listens on http://www.contoso.com and http://contoso.com. It is also useful to create a service that has a base address for internal users and a separate base address for external users.</span></span> <span data-ttu-id="56d2c-106">Příklad: http://internal.contoso.com a http://www.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="56d2c-106">For example: http://internal.contoso.com and http://www.contoso.com.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56d2c-107">Tato funkce je dostupná, pomocí protokolu HTTP jenom.</span><span class="sxs-lookup"><span data-stu-id="56d2c-107">This functionality is only available using the HTTP protocol.</span></span>  
  
## <a name="multiple-base-addresses"></a><span data-ttu-id="56d2c-108">Vícenásobné základní adresy</span><span class="sxs-lookup"><span data-stu-id="56d2c-108">Multiple Base Addresses</span></span>  
 <span data-ttu-id="56d2c-109">Tato funkce je k dispozici pouze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, které jsou hostované v rámci služby IIS.</span><span class="sxs-lookup"><span data-stu-id="56d2c-109">This feature is only available to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services that are hosted under IIS.</span></span> <span data-ttu-id="56d2c-110">Tato funkce není povolená ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="56d2c-110">This feature is not enabled by default.</span></span> <span data-ttu-id="56d2c-111">Povolit, je nutné přidat `multipleSiteBindingsEnabled` atribut <`serviceHostingEnvironment`> element v souboru Web.config souborů a nastavte ji na `true`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="56d2c-111">To enable it you must add the `multipleSiteBindingsEnabled` attribute to the <`serviceHostingEnvironment`> element in your Web.config file and set it to `true`, as shown in the following example.</span></span>  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 <span data-ttu-id="56d2c-112">Při hostování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v rámci služby IIS, služba IIS vytvoří jednu základní adresu, na základě v identifikátoru URI do virtuálního adresáře, která obsahuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="56d2c-112">When hosting a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service under IIS, IIS creates one base address for you based on the URI to the virtual directory that contains the application.</span></span> <span data-ttu-id="56d2c-113">Můžete přidat další základní adresy, které používají stejný protokol pomocí Správce Internetové informační služby přidat jeden nebo více vazby na webové stránky.</span><span class="sxs-lookup"><span data-stu-id="56d2c-113">You can add additional base addresses that use the same protocol by using Internet Information Services Manager to add one or more bindings to your Web site.</span></span> <span data-ttu-id="56d2c-114">Pro každou vazbu zadejte protokol (HTTP nebo HTTPS), adresu IP, portu a názvu hostitele.</span><span class="sxs-lookup"><span data-stu-id="56d2c-114">For each binding specify a protocol (HTTP or HTTPS), an IP address, a port, and a host name.</span></span> <span data-ttu-id="56d2c-115">Další informace o používání Správce Internetové informační služby najdete v tématu [Správce služby IIS (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057).</span><span class="sxs-lookup"><span data-stu-id="56d2c-115">For more information about using Internet Information Services Manager, see [IIS Manager (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057).</span></span> <span data-ttu-id="56d2c-116">Další informace o přidávání vazeb k lokalitě najdete v tématu [vytvoření webového serveru (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)</span><span class="sxs-lookup"><span data-stu-id="56d2c-116">For more information about adding bindings to a site, see [Create a Web Site (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)</span></span>  
  
 <span data-ttu-id="56d2c-117">Zadání více základní adresy pro stejnou lokalitu ovlivňuje obsah [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stránku nápovědy, import schématu a informace WSDL/MEX vygenerované službou.</span><span class="sxs-lookup"><span data-stu-id="56d2c-117">Specifying multiple base addresses for the same site affects the content of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Help page, importing schema, and the WSDL/MEX information generated by the service.</span></span> <span data-ttu-id="56d2c-118">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Zobrazí příkazový řádek, který používá ke generování stránky nápovědy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, který může komunikovat se službou.</span><span class="sxs-lookup"><span data-stu-id="56d2c-118">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Help page displays the command line to use to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that can communicate with the service.</span></span> <span data-ttu-id="56d2c-119">Tento příkaz obsahuje pouze první adresa zadaná v vazby služby IIS pro web.</span><span class="sxs-lookup"><span data-stu-id="56d2c-119">This command line contains only the first address specified in the IIS binding for the Web site.</span></span> <span data-ttu-id="56d2c-120">Podobně když import schématu, pouze první základní adresu určenou v IIS vazby se používá.</span><span class="sxs-lookup"><span data-stu-id="56d2c-120">Similarly when importing schema, only the first base address specified in the IIS binding is used.</span></span> <span data-ttu-id="56d2c-121">WSDL a MEX data obsahovat všechny základní adresami uvedenými v vazby služby IIS.</span><span class="sxs-lookup"><span data-stu-id="56d2c-121">WSDL and MEX data contain all the base addresses specified in the IIS bindings.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="56d2c-122">To znamená, že pokud služba má dvě základní adresy, jednu pro interní uživatele a druhou pro externí uživatele, jsou zadány oba ve schématu WSDL/MEX informace vygenerované službou.</span><span class="sxs-lookup"><span data-stu-id="56d2c-122">This means that if a service has two base addresses, one for internal users and one for external users, both are specified in the WSDL/MEX information generated by the service.</span></span>
