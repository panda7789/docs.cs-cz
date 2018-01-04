---
title: "Přenos a serializace dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8daadec1eef20e62747cdbfcafd1fd13cfc16093
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="ad8ee-102">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="ad8ee-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="ad8ee-103">V systému připojený služeb a klientů závisí na výměnu dat k provedení jakékoli úlohy.</span><span class="sxs-lookup"><span data-stu-id="ad8ee-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="ad8ee-104">Jako vývojář služeb nebo klienta, je potřeba také pochopit, jak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zpracovává data a serializace dat před vytvořením aplikace, které jsou efektivní a snadno spravovat.</span><span class="sxs-lookup"><span data-stu-id="ad8ee-104">As a developer of a service or client, you must also understand how [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad8ee-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ad8ee-105">In This Section</span></span>  
 [<span data-ttu-id="ad8ee-106">Určování přenosu dat v kontraktech služby</span><span class="sxs-lookup"><span data-stu-id="ad8ee-106">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="ad8ee-107">Popisuje základní koncepty přenosu dat do služby.</span><span class="sxs-lookup"><span data-stu-id="ad8ee-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="ad8ee-108">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="ad8ee-108">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="ad8ee-109">Popisuje, jaká data měnící se a jak vytvořit a používat je.</span><span class="sxs-lookup"><span data-stu-id="ad8ee-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="ad8ee-110">Serializátor kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="ad8ee-110">Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <span data-ttu-id="ad8ee-111">Popisuje, jak provést serializace dat pomocí <xref:System.Runtime.Serialization.DataContractSerializer> třídu nebo prodloužení <xref:System.Runtime.Serialization.XmlObjectSerializer> – třída.</span><span class="sxs-lookup"><span data-stu-id="ad8ee-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="ad8ee-112">Používání třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="ad8ee-112">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <span data-ttu-id="ad8ee-113">Popisuje, jak a proč používat <xref:System.Xml.Serialization.XmlSerializer> třídy alternativu k <xref:System.Runtime.Serialization.DataContractSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="ad8ee-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="ad8ee-114">Použití kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="ad8ee-114">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 <span data-ttu-id="ad8ee-115">Popisuje, jak povolit kontrakty zpráv dobrou kontrolu protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="ad8ee-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="ad8ee-116">Používání třídy Message</span><span class="sxs-lookup"><span data-stu-id="ad8ee-116">Using the Message Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 <span data-ttu-id="ad8ee-117">Popisuje, jak používat funkce tříd zprávy.</span><span class="sxs-lookup"><span data-stu-id="ad8ee-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="ad8ee-118">Filtrování</span><span class="sxs-lookup"><span data-stu-id="ad8ee-118">Filtering</span></span>](../../../../docs/framework/wcf/feature-details/filtering.md)  
 <span data-ttu-id="ad8ee-119">Popisuje filtrování, která umožňuje předběžné zpracování zpráv na základě různých kritérií.</span><span class="sxs-lookup"><span data-stu-id="ad8ee-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="ad8ee-120">Objemná data a streamování</span><span class="sxs-lookup"><span data-stu-id="ad8ee-120">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 <span data-ttu-id="ad8ee-121">Popisuje, jak k odeslání velkého bloku dat, jako je binární soubor.</span><span class="sxs-lookup"><span data-stu-id="ad8ee-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="ad8ee-122">Důležité informace o zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="ad8ee-122">Security Considerations for Data</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 <span data-ttu-id="ad8ee-123">Popisuje položky, které budou vědět, když přenos dat a serializace.</span><span class="sxs-lookup"><span data-stu-id="ad8ee-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="ad8ee-124">Strukturální přehled přenosu dat</span><span class="sxs-lookup"><span data-stu-id="ad8ee-124">Data Transfer Architectural Overview</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 <span data-ttu-id="ad8ee-125">Popisuje zobrazení celkového návrhu přenosu dat v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad8ee-125">Describes a view of the overall design of data transfer in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ad8ee-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ad8ee-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="ad8ee-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ad8ee-127">Related Sections</span></span>  
 [<span data-ttu-id="ad8ee-128">Rozšiřování kodérů a serializátorů</span><span class="sxs-lookup"><span data-stu-id="ad8ee-128">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="ad8ee-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad8ee-129">See Also</span></span>  
 [<span data-ttu-id="ad8ee-130">Osvědčené postupy: Správa verzí kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="ad8ee-130">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [<span data-ttu-id="ad8ee-131">Správa verzí služby</span><span class="sxs-lookup"><span data-stu-id="ad8ee-131">Service Versioning</span></span>](../../../../docs/framework/wcf/service-versioning.md)
