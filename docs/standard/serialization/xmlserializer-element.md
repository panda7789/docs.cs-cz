---
title: '&lt;xmlSerializer&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 2770b82f71f3c4b43df4c44f75248e5392c528c2
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45510127"
---
# <a name="ltxmlserializergt-element"></a><span data-ttu-id="29eaa-102">&lt;xmlSerializer&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="29eaa-102">&lt;xmlSerializer&gt; Element</span></span>
<span data-ttu-id="29eaa-103">Určuje, zda dodatečnou kontrolu průběh <xref:System.Xml.Serialization.XmlSerializer> je Hotovo.</span><span class="sxs-lookup"><span data-stu-id="29eaa-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="29eaa-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="29eaa-104">\<configuration></span></span>  
<span data-ttu-id="29eaa-105">\<System.XML.Serialization ></span><span class="sxs-lookup"><span data-stu-id="29eaa-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29eaa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29eaa-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29eaa-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="29eaa-107">Attributes and Elements</span></span>  
 <span data-ttu-id="29eaa-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="29eaa-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29eaa-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="29eaa-109">Attributes</span></span>  
  
|<span data-ttu-id="29eaa-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="29eaa-110">Attribute</span></span>|<span data-ttu-id="29eaa-111">Popis</span><span class="sxs-lookup"><span data-stu-id="29eaa-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29eaa-112">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="29eaa-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="29eaa-113">Určuje, zda průběh <xref:System.Xml.Serialization.XmlSerializer> je zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="29eaa-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="29eaa-114">Nastavte atribut na "true" nebo "false".</span><span class="sxs-lookup"><span data-stu-id="29eaa-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="29eaa-115">Výchozí hodnota je "true".</span><span class="sxs-lookup"><span data-stu-id="29eaa-115">The default is "true".</span></span>|  
|<span data-ttu-id="29eaa-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="29eaa-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="29eaa-117">Určuje, zda <xref:System.Xml.Serialization.XmlSerializer> používá starší verze serializace generace, který generuje sestavení tak, že zápis do souboru kódu jazyka C# a jeho kompilace na sestavení.</span><span class="sxs-lookup"><span data-stu-id="29eaa-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="29eaa-118">Výchozí hodnota je **false**.</span><span class="sxs-lookup"><span data-stu-id="29eaa-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29eaa-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="29eaa-119">Child Elements</span></span>  
 <span data-ttu-id="29eaa-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="29eaa-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29eaa-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="29eaa-121">Parent Elements</span></span>  
  
|<span data-ttu-id="29eaa-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="29eaa-122">Element</span></span>|<span data-ttu-id="29eaa-123">Popis</span><span class="sxs-lookup"><span data-stu-id="29eaa-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29eaa-124">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="29eaa-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="29eaa-125">Obsahuje nastavení konfigurace pro <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.</span><span class="sxs-lookup"><span data-stu-id="29eaa-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29eaa-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29eaa-126">Remarks</span></span>  
 <span data-ttu-id="29eaa-127">Ve výchozím nastavení <xref:System.Xml.Serialization.XmlSerializer> poskytuje další vrstvu zabezpečení proti potenciální odmítnutí útoků služby při deserializaci nedůvěryhodná data.</span><span class="sxs-lookup"><span data-stu-id="29eaa-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="29eaa-128">Učiní tak pokusem o detekovat nekonečné smyčce během deserializace.</span><span class="sxs-lookup"><span data-stu-id="29eaa-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="29eaa-129">Pokud je zjištěno takovou podmínku, je vyvolána výjimka s následující zprávou: "došlo k vnitřní chybě: deserializace se nezdařila lze postoupit nad základního datového proudu."</span><span class="sxs-lookup"><span data-stu-id="29eaa-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="29eaa-130">Přijetí tato zpráva nemusí znamenat, že útoku služby probíhá.</span><span class="sxs-lookup"><span data-stu-id="29eaa-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="29eaa-131">V některých výjimečných případech mechanismus detekce nekonečné smyčce vytváří chybné detekce a legitimní příchozí zprávy, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="29eaa-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="29eaa-132">Pokud zjistíte, že v aplikaci konkrétní legitimní zprávy jsou odmítnuta, podle této další úroveň ochrany, nastavte **checkDeserializeAdvances** atribut "false".</span><span class="sxs-lookup"><span data-stu-id="29eaa-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="29eaa-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="29eaa-133">Example</span></span>  
 <span data-ttu-id="29eaa-134">Následující příklad kódu nastaví **checkDeserializeAdvances** atribut "false".</span><span class="sxs-lookup"><span data-stu-id="29eaa-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="29eaa-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29eaa-135">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>  
- [<span data-ttu-id="29eaa-136">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="29eaa-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
- [<span data-ttu-id="29eaa-137">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="29eaa-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
