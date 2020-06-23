---
title: Zabezpečení přenosu
description: Pomocí těchto odkazů můžete pochopit mechanismy zabezpečení přenosu v WFC, způsob jejich implementace a jejich možnosti.
ms.date: 03/30/2017
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
ms.openlocfilehash: d39aa49906b79b9e12eecf04629080863719f986
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244748"
---
# <a name="transport-security"></a><span data-ttu-id="1265e-103">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="1265e-103">Transport Security</span></span>
<span data-ttu-id="1265e-104">Zabezpečení přenosu v Windows Communication Foundation (WCF) závisí na vybrané vazbě.</span><span class="sxs-lookup"><span data-stu-id="1265e-104">Transport security in Windows Communication Foundation (WCF) depends on the binding selected.</span></span> <span data-ttu-id="1265e-105">Přenos, který implementuje vazba, určuje skutečný bezpečnostní mechanismus.</span><span class="sxs-lookup"><span data-stu-id="1265e-105">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="1265e-106">Témata v této části popisují implementované mechanismy a jejich možnosti.</span><span class="sxs-lookup"><span data-stu-id="1265e-106">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1265e-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1265e-107">In This Section</span></span>  
 [<span data-ttu-id="1265e-108">Přehled zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="1265e-108">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="1265e-109">Vysvětluje základy zabezpečení přenosu ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="1265e-109">Explains the basics of transport security in WCF.</span></span>  
  
 [<span data-ttu-id="1265e-110">Zabezpečení přenosu HTTP</span><span class="sxs-lookup"><span data-stu-id="1265e-110">HTTP Transport Security</span></span>](http-transport-security.md)  
 <span data-ttu-id="1265e-111">Vysvětluje, jak WCF implementuje SSL (Secure Sockets Layer) (SSL nebo HTTPS).</span><span class="sxs-lookup"><span data-stu-id="1265e-111">Explains how WCF implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="1265e-112">Princip ověřování HTTP</span><span class="sxs-lookup"><span data-stu-id="1265e-112">Understanding HTTP Authentication</span></span>](understanding-http-authentication.md)  
 <span data-ttu-id="1265e-113">Popisuje schémata ověřování HTTP, například Basic, Digest, NT LAN Manager (NTLM) a další.</span><span class="sxs-lookup"><span data-stu-id="1265e-113">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="1265e-114">Použití zosobnění se zabezpečením přenosu</span><span class="sxs-lookup"><span data-stu-id="1265e-114">Using Impersonation with Transport Security</span></span>](using-impersonation-with-transport-security.md)  
 <span data-ttu-id="1265e-115">Vysvětluje pět úrovní zosobnění, které je možné v režimu zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="1265e-115">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="1265e-116">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="1265e-116">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="1265e-117">Provede vás základy konfigurace portu na počítači s certifikátem X. 509 pro zabezpečení SSL (Transport).</span><span class="sxs-lookup"><span data-stu-id="1265e-117">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1265e-118">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="1265e-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="1265e-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1265e-119">Related Sections</span></span>  
 [<span data-ttu-id="1265e-120">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="1265e-120">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="1265e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="1265e-121">See also</span></span>

- [<span data-ttu-id="1265e-122">Programování zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="1265e-122">Programming WCF Security</span></span>](programming-wcf-security.md)
