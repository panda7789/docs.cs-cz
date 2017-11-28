---
title: "&lt;xmlSerializer&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cadca32d5aa34d5cb6f9091f65c34c7cba603ff5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltxmlserializergt-element"></a><span data-ttu-id="cab68-102">&lt;xmlSerializer&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="cab68-102">&lt;xmlSerializer&gt; Element</span></span>
<span data-ttu-id="cab68-103">Určuje, zda dodatečnou kontrolu průběh <xref:System.Xml.Serialization.XmlSerializer> je Hotovo.</span><span class="sxs-lookup"><span data-stu-id="cab68-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="cab68-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="cab68-104">\<configuration></span></span>  
<span data-ttu-id="cab68-105">\<System.XML.Serialization ></span><span class="sxs-lookup"><span data-stu-id="cab68-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cab68-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cab68-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cab68-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cab68-107">Attributes and Elements</span></span>  
 <span data-ttu-id="cab68-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cab68-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cab68-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="cab68-109">Attributes</span></span>  
  
|<span data-ttu-id="cab68-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="cab68-110">Attribute</span></span>|<span data-ttu-id="cab68-111">Popis</span><span class="sxs-lookup"><span data-stu-id="cab68-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cab68-112">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="cab68-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="cab68-113">Určuje, zda průběh <xref:System.Xml.Serialization.XmlSerializer> je zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="cab68-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="cab68-114">Nastavte atribut na "true" nebo "false".</span><span class="sxs-lookup"><span data-stu-id="cab68-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="cab68-115">Výchozí hodnota je "true".</span><span class="sxs-lookup"><span data-stu-id="cab68-115">The default is "true".</span></span>|  
|<span data-ttu-id="cab68-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="cab68-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="cab68-117">Určuje, zda <xref:System.Xml.Serialization.XmlSerializer> používá starší verze serializace generace, který generuje sestavení tak, že zápis do souboru kódu jazyka C# a jeho kompilace na sestavení.</span><span class="sxs-lookup"><span data-stu-id="cab68-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="cab68-118">Výchozí hodnota je **false**.</span><span class="sxs-lookup"><span data-stu-id="cab68-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cab68-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cab68-119">Child Elements</span></span>  
 <span data-ttu-id="cab68-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="cab68-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cab68-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cab68-121">Parent Elements</span></span>  
  
|<span data-ttu-id="cab68-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="cab68-122">Element</span></span>|<span data-ttu-id="cab68-123">Popis</span><span class="sxs-lookup"><span data-stu-id="cab68-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cab68-124">\<System.XML.Serialization > elementu</span><span class="sxs-lookup"><span data-stu-id="cab68-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="cab68-125">Obsahuje nastavení konfigurace pro <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.</span><span class="sxs-lookup"><span data-stu-id="cab68-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cab68-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cab68-126">Remarks</span></span>  
 <span data-ttu-id="cab68-127">Ve výchozím nastavení <xref:System.Xml.Serialization.XmlSerializer> poskytuje další vrstvu zabezpečení proti potenciální odmítnutí útoků služby při deserializaci nedůvěryhodná data.</span><span class="sxs-lookup"><span data-stu-id="cab68-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="cab68-128">Učiní tak pokusem o detekovat nekonečné smyčce během deserializace.</span><span class="sxs-lookup"><span data-stu-id="cab68-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="cab68-129">Pokud je zjištěn takovém stavu, je vyvolána výjimka s následující zprávou: "vnitřní chyba: deserializace posunutí přes základního datového proudu se nezdařilo."</span><span class="sxs-lookup"><span data-stu-id="cab68-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="cab68-130">Přijetí tato zpráva nemusí znamenat, že útoku služby probíhá.</span><span class="sxs-lookup"><span data-stu-id="cab68-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="cab68-131">V některých výjimečných případech mechanismus detekce nekonečné smyčce vytváří chybné detekce a legitimní příchozí zprávy, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="cab68-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="cab68-132">Pokud zjistíte, že v konkrétní aplikaci legitimní zprávy se odmítne tento další úroveň ochrany, nastavte **checkDeserializeAdvances** atributu na hodnotu "false".</span><span class="sxs-lookup"><span data-stu-id="cab68-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="cab68-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="cab68-133">Example</span></span>  
 <span data-ttu-id="cab68-134">Následující příklad kódu nastaví **checkDeserializeAdvances** atributu na hodnotu "false".</span><span class="sxs-lookup"><span data-stu-id="cab68-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cab68-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="cab68-135">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="cab68-136">\<System.XML.Serialization > elementu</span><span class="sxs-lookup"><span data-stu-id="cab68-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="cab68-137">XML a serializace protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="cab68-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
