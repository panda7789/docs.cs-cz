---
title: Element <xmlSerializer>
description: <xmlSerializer>Prvek určuje, zda je provedena dodatečná kontrolní průběh objektu XmlSerializer.
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 667d59f7eb0d1c7682afcdda584cc5b0ca2da802
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288924"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="2b9f9-103">Element \<xmlSerializer></span><span class="sxs-lookup"><span data-stu-id="2b9f9-103">\<xmlSerializer> Element</span></span>
<span data-ttu-id="2b9f9-104">Určuje, zda dodatečnou kontrolu průběh <xref:System.Xml.Serialization.XmlSerializer> je Hotovo.</span><span class="sxs-lookup"><span data-stu-id="2b9f9-104">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 \<configuration>  
\<system.xml.serialization>  
  
## <a name="syntax"></a><span data-ttu-id="2b9f9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b9f9-105">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b9f9-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2b9f9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2b9f9-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2b9f9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b9f9-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="2b9f9-108">Attributes</span></span>  
  
|<span data-ttu-id="2b9f9-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="2b9f9-109">Attribute</span></span>|<span data-ttu-id="2b9f9-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2b9f9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b9f9-111">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="2b9f9-111">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="2b9f9-112">Určuje, zda průběh <xref:System.Xml.Serialization.XmlSerializer> je zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="2b9f9-112">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="2b9f9-113">Nastavte atribut na "true" nebo "false".</span><span class="sxs-lookup"><span data-stu-id="2b9f9-113">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="2b9f9-114">Výchozí hodnota je "true".</span><span class="sxs-lookup"><span data-stu-id="2b9f9-114">The default is "true".</span></span>|  
|<span data-ttu-id="2b9f9-115">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="2b9f9-115">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="2b9f9-116">Určuje, zda <xref:System.Xml.Serialization.XmlSerializer> používá starší verze serializace generace, který generuje sestavení tak, že zápis do souboru kódu jazyka C# a jeho kompilace na sestavení.</span><span class="sxs-lookup"><span data-stu-id="2b9f9-116">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="2b9f9-117">Výchozí hodnota je **false**.</span><span class="sxs-lookup"><span data-stu-id="2b9f9-117">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b9f9-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2b9f9-118">Child Elements</span></span>  
 <span data-ttu-id="2b9f9-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="2b9f9-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b9f9-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2b9f9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2b9f9-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="2b9f9-121">Element</span></span>|<span data-ttu-id="2b9f9-122">Popis</span><span class="sxs-lookup"><span data-stu-id="2b9f9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b9f9-123">\<system.xml.serialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="2b9f9-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="2b9f9-124">Obsahuje nastavení konfigurace pro <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.</span><span class="sxs-lookup"><span data-stu-id="2b9f9-124">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b9f9-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b9f9-125">Remarks</span></span>  
 <span data-ttu-id="2b9f9-126">Ve výchozím nastavení <xref:System.Xml.Serialization.XmlSerializer> poskytuje další vrstvu zabezpečení proti potenciální odmítnutí útoků služby při deserializaci nedůvěryhodná data.</span><span class="sxs-lookup"><span data-stu-id="2b9f9-126">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="2b9f9-127">Učiní tak pokusem o detekovat nekonečné smyčce během deserializace.</span><span class="sxs-lookup"><span data-stu-id="2b9f9-127">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="2b9f9-128">Je-li taková podmínka zjištěna, je vyvolána výjimka s následující zprávou: "vnitřní chyba: deserializace nemohla pokračovat v podkladovém datovém proudu".</span><span class="sxs-lookup"><span data-stu-id="2b9f9-128">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="2b9f9-129">Přijetí tato zpráva nemusí znamenat, že útoku služby probíhá.</span><span class="sxs-lookup"><span data-stu-id="2b9f9-129">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="2b9f9-130">V některých výjimečných případech mechanismus detekce nekonečné smyčce vytváří chybné detekce a legitimní příchozí zprávy, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2b9f9-130">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="2b9f9-131">Pokud zjistíte, že v rámci konkrétní aplikace jsou legitimní zprávy odmítnuty touto dodatečnou vrstvou ochrany, nastavte atribut **checkDeserializeAdvances** na hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="2b9f9-131">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b9f9-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b9f9-132">Example</span></span>  
 <span data-ttu-id="2b9f9-133">Následující příklad kódu nastaví atribut **checkDeserializeAdvances** na hodnotu false (NEPRAVDA).</span><span class="sxs-lookup"><span data-stu-id="2b9f9-133">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b9f9-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b9f9-134">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="2b9f9-135">\<system.xml.serialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="2b9f9-135">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="2b9f9-136">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="2b9f9-136">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
