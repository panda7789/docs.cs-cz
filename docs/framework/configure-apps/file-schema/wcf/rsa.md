---
title: '&lt;RSA&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c382cb6c28825bdf590017cda986a576311423af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltrsagt"></a><span data-ttu-id="6d191-102">&lt;RSA&gt;</span><span class="sxs-lookup"><span data-stu-id="6d191-102">&lt;rsa&gt;</span></span>
<span data-ttu-id="6d191-103">Zabezpečené klienta WCF, která se připojuje k koncový bod s tuto identitu ověřuje, že deklarací identity předkládaných serverem obsahují deklarace identity, který obsahuje veřejný klíč RSA použitý k vytvoření tuto identitu.</span><span class="sxs-lookup"><span data-stu-id="6d191-103">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="6d191-104">\<identity ></span><span class="sxs-lookup"><span data-stu-id="6d191-104">\<identity></span></span>  
<span data-ttu-id="6d191-105">\<RSA ></span><span class="sxs-lookup"><span data-stu-id="6d191-105">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d191-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d191-106">Syntax</span></span>  
  
```xml  
<rsa value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d191-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6d191-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6d191-108">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6d191-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d191-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="6d191-109">Attributes</span></span>  
  
|<span data-ttu-id="6d191-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="6d191-110">Attribute</span></span>|<span data-ttu-id="6d191-111">Popis</span><span class="sxs-lookup"><span data-stu-id="6d191-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d191-112">value</span><span class="sxs-lookup"><span data-stu-id="6d191-112">value</span></span>|<span data-ttu-id="6d191-113">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="6d191-113">Optional String.</span></span> <span data-ttu-id="6d191-114">RSA veřejného klíče hodnota být porovnána s na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="6d191-114">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d191-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6d191-115">Child Elements</span></span>  
 <span data-ttu-id="6d191-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="6d191-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d191-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6d191-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6d191-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d191-118">Element</span></span>|<span data-ttu-id="6d191-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6d191-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d191-120">\<identity ></span><span class="sxs-lookup"><span data-stu-id="6d191-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="6d191-121">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="6d191-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d191-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d191-122">Remarks</span></span>  
 <span data-ttu-id="6d191-123">Kontrolu RSA umožňuje konkrétně omezit ověření na jeden certifikát na základě jeho klíče RSA nebo vygenerovat vlastní hodnota klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="6d191-123">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="6d191-124">Toto umožňuje přísnější ověřování konkrétního klíče RSA za cenu službu už ve spolupráci s existující klienti změnu hodnoty klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="6d191-124">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="6d191-125">Další informace o používání identity k ověření služby klienta najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6d191-125">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d191-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d191-126">Example</span></span>  
 <span data-ttu-id="6d191-127">Následující kód konfigurace určuje hodnota veřejného klíče certifikátu X.509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="6d191-127">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <rsa value = "0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"/>  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d191-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d191-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.RsaEndpointIdentity>  
 [<span data-ttu-id="6d191-129">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="6d191-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="6d191-130">\<identity ></span><span class="sxs-lookup"><span data-stu-id="6d191-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
