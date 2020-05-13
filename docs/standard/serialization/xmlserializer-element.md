---
title: Element <xmlSerializer>
description: <xmlSerializer>Prvek určuje, zda je provedena dodatečná kontrolní průběh objektu XmlSerializer.
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 68037959893ec307a896ea86d21e40a9d7aa824c
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380023"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="d273d-103">\<xmlSerializer – element> elementu</span><span class="sxs-lookup"><span data-stu-id="d273d-103">\<xmlSerializer> Element</span></span>
<span data-ttu-id="d273d-104">Určuje, zda dodatečnou kontrolu průběh <xref:System.Xml.Serialization.XmlSerializer> je Hotovo.</span><span class="sxs-lookup"><span data-stu-id="d273d-104">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="d273d-105">\<> konfigurace</span><span class="sxs-lookup"><span data-stu-id="d273d-105">\<configuration></span></span>  
<span data-ttu-id="d273d-106">\<System. XML. Serialization –></span><span class="sxs-lookup"><span data-stu-id="d273d-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d273d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d273d-107">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d273d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d273d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d273d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d273d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d273d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d273d-110">Attributes</span></span>  
  
|<span data-ttu-id="d273d-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d273d-111">Attribute</span></span>|<span data-ttu-id="d273d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d273d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d273d-113">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="d273d-113">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="d273d-114">Určuje, zda průběh <xref:System.Xml.Serialization.XmlSerializer> je zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="d273d-114">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="d273d-115">Nastavte atribut na "true" nebo "false".</span><span class="sxs-lookup"><span data-stu-id="d273d-115">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="d273d-116">Výchozí hodnota je "true".</span><span class="sxs-lookup"><span data-stu-id="d273d-116">The default is "true".</span></span>|  
|<span data-ttu-id="d273d-117">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="d273d-117">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="d273d-118">Určuje, zda <xref:System.Xml.Serialization.XmlSerializer> používá starší verze serializace generace, který generuje sestavení tak, že zápis do souboru kódu jazyka C# a jeho kompilace na sestavení.</span><span class="sxs-lookup"><span data-stu-id="d273d-118">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="d273d-119">Výchozí hodnota je **false**.</span><span class="sxs-lookup"><span data-stu-id="d273d-119">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d273d-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d273d-120">Child Elements</span></span>  
 <span data-ttu-id="d273d-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="d273d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d273d-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d273d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d273d-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="d273d-123">Element</span></span>|<span data-ttu-id="d273d-124">Popis</span><span class="sxs-lookup"><span data-stu-id="d273d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d273d-125">\<System. XML. Serialization – element></span><span class="sxs-lookup"><span data-stu-id="d273d-125">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="d273d-126">Obsahuje nastavení konfigurace pro <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.</span><span class="sxs-lookup"><span data-stu-id="d273d-126">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d273d-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d273d-127">Remarks</span></span>  
 <span data-ttu-id="d273d-128">Ve výchozím nastavení <xref:System.Xml.Serialization.XmlSerializer> poskytuje další vrstvu zabezpečení proti potenciální odmítnutí útoků služby při deserializaci nedůvěryhodná data.</span><span class="sxs-lookup"><span data-stu-id="d273d-128">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="d273d-129">Učiní tak pokusem o detekovat nekonečné smyčce během deserializace.</span><span class="sxs-lookup"><span data-stu-id="d273d-129">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="d273d-130">Je-li taková podmínka zjištěna, je vyvolána výjimka s následující zprávou: "vnitřní chyba: deserializace nemohla pokračovat v podkladovém datovém proudu".</span><span class="sxs-lookup"><span data-stu-id="d273d-130">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="d273d-131">Přijetí tato zpráva nemusí znamenat, že útoku služby probíhá.</span><span class="sxs-lookup"><span data-stu-id="d273d-131">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="d273d-132">V některých výjimečných případech mechanismus detekce nekonečné smyčce vytváří chybné detekce a legitimní příchozí zprávy, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d273d-132">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="d273d-133">Pokud zjistíte, že v rámci konkrétní aplikace jsou legitimní zprávy odmítnuty touto dodatečnou vrstvou ochrany, nastavte atribut **checkDeserializeAdvances** na hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="d273d-133">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="d273d-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="d273d-134">Example</span></span>  
 <span data-ttu-id="d273d-135">Následující příklad kódu nastaví atribut **checkDeserializeAdvances** na hodnotu false (NEPRAVDA).</span><span class="sxs-lookup"><span data-stu-id="d273d-135">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d273d-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="d273d-136">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="d273d-137">\<System. XML. Serialization – element></span><span class="sxs-lookup"><span data-stu-id="d273d-137">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="d273d-138">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="d273d-138">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
