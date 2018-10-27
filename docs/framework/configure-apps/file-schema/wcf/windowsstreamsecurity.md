---
title: '&lt;zabezpečení windowsstreamsecurity iniciuje&gt;'
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: e117c30ba2583158ee21fd11ff4a38b094c18fd9
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50045925"
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="5a73e-102">&lt;zabezpečení windowsstreamsecurity iniciuje&gt;</span><span class="sxs-lookup"><span data-stu-id="5a73e-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="5a73e-103">Zadejte nastavení zabezpečení datového proudu Windows pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="5a73e-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="5a73e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5a73e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5a73e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="5a73e-105">\<bindings></span></span>  
<span data-ttu-id="5a73e-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="5a73e-106">\<customBinding></span></span>  
<span data-ttu-id="5a73e-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="5a73e-107">\<binding></span></span>  
<span data-ttu-id="5a73e-108">\<zabezpečení windowsstreamsecurity iniciuje ></span><span class="sxs-lookup"><span data-stu-id="5a73e-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a73e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a73e-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a73e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a73e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a73e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5a73e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a73e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a73e-112">Attributes</span></span>  
  
|<span data-ttu-id="5a73e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5a73e-113">Attribute</span></span>|<span data-ttu-id="5a73e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5a73e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a73e-115">Třída protectionLevel</span><span class="sxs-lookup"><span data-stu-id="5a73e-115">protectionLevel</span></span>|<span data-ttu-id="5a73e-116">Definuje zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="5a73e-116">Defines message-level security.</span></span> <span data-ttu-id="5a73e-117">Podepisování zpráv snižuje riziko manipulace s zprávy při jejich přenosu od jiných dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="5a73e-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="5a73e-118">Šifrování poskytuje data úrovně ochrany osobních údajů při přenosu.</span><span class="sxs-lookup"><span data-stu-id="5a73e-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="5a73e-119">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="5a73e-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5a73e-120">-Žádný: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="5a73e-120">-   None: No protection.</span></span><br /><span data-ttu-id="5a73e-121">-Sign: Jsou podepsané zprávy.</span><span class="sxs-lookup"><span data-stu-id="5a73e-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="5a73e-122">-EncryptAndSign: Podepsaný a zašifrovaný zpráv.</span><span class="sxs-lookup"><span data-stu-id="5a73e-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="5a73e-123">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="5a73e-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="5a73e-124">Tento atribut je typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="5a73e-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a73e-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a73e-125">Child Elements</span></span>  
 <span data-ttu-id="5a73e-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a73e-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a73e-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a73e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5a73e-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a73e-128">Element</span></span>|<span data-ttu-id="5a73e-129">Popis</span><span class="sxs-lookup"><span data-stu-id="5a73e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a73e-130">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="5a73e-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="5a73e-131">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="5a73e-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a73e-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a73e-132">Remarks</span></span>  
 <span data-ttu-id="5a73e-133">Na základě datového proudu přenosu inovace podporují přenosy, které používají protokol orientovaný na stream jako je například TCP a pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="5a73e-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="5a73e-134">Konkrétně WCF poskytuje upgradů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5a73e-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="5a73e-135">Konfigurace tohoto zabezpečení přenosu jsou zapouzdřena objektem tento prvek konfigurace a také zobrazením [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), které se konfigurují a přidat do vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="5a73e-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a73e-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a73e-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="5a73e-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="5a73e-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5a73e-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="5a73e-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="5a73e-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="5a73e-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="5a73e-140">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="5a73e-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
