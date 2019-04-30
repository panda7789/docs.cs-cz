---
title: Přenos a serializace dat
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 1eefd82a149d0bc215ca441e92c7d737a744b1e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856554"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="2d37b-102">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="2d37b-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="2d37b-103">V připojené systému služeb a klientů závisí na výměny dat k provedení jakékoli úlohy.</span><span class="sxs-lookup"><span data-stu-id="2d37b-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="2d37b-104">Jako vývojář službu nebo klienta musíte pochopit, jak Windows Communication Foundation (WCF) zpracovává data a serializace dat k vytvoření aplikace, které jsou efektivní a snadno udržovat.</span><span class="sxs-lookup"><span data-stu-id="2d37b-104">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d37b-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2d37b-105">In This Section</span></span>  
 [<span data-ttu-id="2d37b-106">Určování přenosu dat v kontraktech služby</span><span class="sxs-lookup"><span data-stu-id="2d37b-106">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="2d37b-107">Popisuje základní koncepty přenosy dat služby.</span><span class="sxs-lookup"><span data-stu-id="2d37b-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="2d37b-108">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="2d37b-108">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="2d37b-109">Popisuje, jaká data smluv jsou a tom, jak vytvořit a použít je.</span><span class="sxs-lookup"><span data-stu-id="2d37b-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="2d37b-110">Serializátor kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="2d37b-110">Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <span data-ttu-id="2d37b-111">Popisuje, jak provést serializace dat pomocí <xref:System.Runtime.Serialization.DataContractSerializer> třídy nebo jakéhokoli rozšíření <xref:System.Runtime.Serialization.XmlObjectSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="2d37b-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="2d37b-112">Používání třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="2d37b-112">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <span data-ttu-id="2d37b-113">Popisuje, jak a proč používat <xref:System.Xml.Serialization.XmlSerializer> třídy, je alternativou k <xref:System.Runtime.Serialization.DataContractSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="2d37b-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="2d37b-114">Použití kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="2d37b-114">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 <span data-ttu-id="2d37b-115">Popisuje, jak povolit kontraktů zpráv přesné řízení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="2d37b-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="2d37b-116">Používání třídy Message</span><span class="sxs-lookup"><span data-stu-id="2d37b-116">Using the Message Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 <span data-ttu-id="2d37b-117">Popisuje, jak používat funkce třídy zpráv.</span><span class="sxs-lookup"><span data-stu-id="2d37b-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="2d37b-118">Filtrování</span><span class="sxs-lookup"><span data-stu-id="2d37b-118">Filtering</span></span>](../../../../docs/framework/wcf/feature-details/filtering.md)  
 <span data-ttu-id="2d37b-119">Popisuje, filtrování, která umožňuje předběžné zpracování zprávy na základě různých kritérií.</span><span class="sxs-lookup"><span data-stu-id="2d37b-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="2d37b-120">Objemná data a streamování</span><span class="sxs-lookup"><span data-stu-id="2d37b-120">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 <span data-ttu-id="2d37b-121">Popisuje postup odesílání velkých blok dat, jako je například binární soubor.</span><span class="sxs-lookup"><span data-stu-id="2d37b-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="2d37b-122">Důležité informace o zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="2d37b-122">Security Considerations for Data</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 <span data-ttu-id="2d37b-123">Popisuje položky, které chcete mít na paměti při programování přenos a serializace dat.</span><span class="sxs-lookup"><span data-stu-id="2d37b-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="2d37b-124">Strukturální přehled přenosu dat</span><span class="sxs-lookup"><span data-stu-id="2d37b-124">Data Transfer Architectural Overview</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 <span data-ttu-id="2d37b-125">Popisuje zobrazení celkového návrhu přenosu dat ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="2d37b-125">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2d37b-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2d37b-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="2d37b-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2d37b-127">Related Sections</span></span>  
 [<span data-ttu-id="2d37b-128">Rozšiřování kodérů a serializátorů</span><span class="sxs-lookup"><span data-stu-id="2d37b-128">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d37b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d37b-129">See also</span></span>

- [<span data-ttu-id="2d37b-130">Osvědčené postupy: Správa verzí kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="2d37b-130">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [<span data-ttu-id="2d37b-131">Správa verzí služby</span><span class="sxs-lookup"><span data-stu-id="2d37b-131">Service Versioning</span></span>](../../../../docs/framework/wcf/service-versioning.md)
