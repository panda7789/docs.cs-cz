---
title: Přenos a serializace dat
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: b07937b0a94c24a934b17d6cf21b726ee0d4362e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593481"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="49b0f-102">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="49b0f-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="49b0f-103">V připojeném systému jsou služby a klienti závislé na výměně dat za účelem provedení jakékoli úlohy.</span><span class="sxs-lookup"><span data-stu-id="49b0f-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="49b0f-104">Jako vývojář služby nebo klienta musíte taky pochopit, jak Windows Communication Foundation (WCF) zpracovává data a serializaci dat, aby bylo možné vytvářet aplikace, které jsou efektivní a snadno se udržují.</span><span class="sxs-lookup"><span data-stu-id="49b0f-104">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49b0f-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="49b0f-105">In This Section</span></span>  
 [<span data-ttu-id="49b0f-106">Určování přenosu dat v kontraktech služby</span><span class="sxs-lookup"><span data-stu-id="49b0f-106">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="49b0f-107">Popisuje základní koncepty přenosu dat v rámci služeb.</span><span class="sxs-lookup"><span data-stu-id="49b0f-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="49b0f-108">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="49b0f-108">Using Data Contracts</span></span>](using-data-contracts.md)  
 <span data-ttu-id="49b0f-109">Popisuje, jaké jsou kontrakty dat a jak je vytvořit a používat.</span><span class="sxs-lookup"><span data-stu-id="49b0f-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="49b0f-110">Serializátor kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="49b0f-110">Data Contract Serializer</span></span>](data-contract-serializer.md)  
 <span data-ttu-id="49b0f-111">Popisuje, jak provést serializaci dat s <xref:System.Runtime.Serialization.DataContractSerializer> třídou nebo libovolným rozšířením <xref:System.Runtime.Serialization.XmlObjectSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="49b0f-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="49b0f-112">Používání třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="49b0f-112">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)  
 <span data-ttu-id="49b0f-113">Popisuje, jak a proč použít <xref:System.Xml.Serialization.XmlSerializer> třídu, alternativu ke <xref:System.Runtime.Serialization.DataContractSerializer> třídě.</span><span class="sxs-lookup"><span data-stu-id="49b0f-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="49b0f-114">Použití kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="49b0f-114">Using Message Contracts</span></span>](using-message-contracts.md)  
 <span data-ttu-id="49b0f-115">Popisuje, jak kontrakty zpráv umožňují přesné řízení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="49b0f-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="49b0f-116">Používání třídy Message</span><span class="sxs-lookup"><span data-stu-id="49b0f-116">Using the Message Class</span></span>](using-the-message-class.md)  
 <span data-ttu-id="49b0f-117">Popisuje, jak používat funkce třídy zpráv.</span><span class="sxs-lookup"><span data-stu-id="49b0f-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="49b0f-118">Filtrování</span><span class="sxs-lookup"><span data-stu-id="49b0f-118">Filtering</span></span>](filtering.md)  
 <span data-ttu-id="49b0f-119">Popisuje filtrování, které umožňuje předběžné zpracování zprávy na základě různých kritérií.</span><span class="sxs-lookup"><span data-stu-id="49b0f-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="49b0f-120">Objemná data a streamování</span><span class="sxs-lookup"><span data-stu-id="49b0f-120">Large Data and Streaming</span></span>](large-data-and-streaming.md)  
 <span data-ttu-id="49b0f-121">Popisuje, jak odeslat velký blok dat, jako je například binární soubor.</span><span class="sxs-lookup"><span data-stu-id="49b0f-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="49b0f-122">Důležité informace o zabezpečení pro data</span><span class="sxs-lookup"><span data-stu-id="49b0f-122">Security Considerations for Data</span></span>](security-considerations-for-data.md)  
 <span data-ttu-id="49b0f-123">Popisuje položky, které je třeba znát při přenosu a serializaci dat programování.</span><span class="sxs-lookup"><span data-stu-id="49b0f-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="49b0f-124">Strukturální přehled přenosu dat</span><span class="sxs-lookup"><span data-stu-id="49b0f-124">Data Transfer Architectural Overview</span></span>](data-transfer-architectural-overview.md)  
 <span data-ttu-id="49b0f-125">Popisuje zobrazení celkového návrhu přenosu dat v rámci služby WCF.</span><span class="sxs-lookup"><span data-stu-id="49b0f-125">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="49b0f-126">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="49b0f-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="49b0f-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="49b0f-127">Related Sections</span></span>  
 [<span data-ttu-id="49b0f-128">Rozšiřování kodérů a serializátorů</span><span class="sxs-lookup"><span data-stu-id="49b0f-128">Extending Encoders and Serializers</span></span>](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="49b0f-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="49b0f-129">See also</span></span>

- [<span data-ttu-id="49b0f-130">Osvědčené postupy: Správa verzí kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="49b0f-130">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)
- [<span data-ttu-id="49b0f-131">Správa verzí služby</span><span class="sxs-lookup"><span data-stu-id="49b0f-131">Service Versioning</span></span>](../service-versioning.md)
