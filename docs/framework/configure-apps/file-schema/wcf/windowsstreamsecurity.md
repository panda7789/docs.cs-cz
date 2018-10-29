---
title: '&lt;zabezpečení windowsstreamsecurity iniciuje&gt;'
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: e117c30ba2583158ee21fd11ff4a38b094c18fd9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197629"
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="b1e2c-102">&lt;zabezpečení windowsstreamsecurity iniciuje&gt;</span><span class="sxs-lookup"><span data-stu-id="b1e2c-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="b1e2c-103">Zadejte nastavení zabezpečení datového proudu Windows pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="b1e2c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b1e2c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b1e2c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b1e2c-105">\<bindings></span></span>  
<span data-ttu-id="b1e2c-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="b1e2c-106">\<customBinding></span></span>  
<span data-ttu-id="b1e2c-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="b1e2c-107">\<binding></span></span>  
<span data-ttu-id="b1e2c-108">\<zabezpečení windowsstreamsecurity iniciuje ></span><span class="sxs-lookup"><span data-stu-id="b1e2c-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e2c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1e2c-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1e2c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b1e2c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b1e2c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1e2c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b1e2c-112">Attributes</span></span>  
  
|<span data-ttu-id="b1e2c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="b1e2c-113">Attribute</span></span>|<span data-ttu-id="b1e2c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b1e2c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1e2c-115">Třída protectionLevel</span><span class="sxs-lookup"><span data-stu-id="b1e2c-115">protectionLevel</span></span>|<span data-ttu-id="b1e2c-116">Definuje zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-116">Defines message-level security.</span></span> <span data-ttu-id="b1e2c-117">Podepisování zpráv snižuje riziko manipulace s zprávy při jejich přenosu od jiných dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="b1e2c-118">Šifrování poskytuje data úrovně ochrany osobních údajů při přenosu.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="b1e2c-119">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="b1e2c-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b1e2c-120">-Žádný: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-120">-   None: No protection.</span></span><br /><span data-ttu-id="b1e2c-121">-Sign: Jsou podepsané zprávy.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="b1e2c-122">-EncryptAndSign: Podepsaný a zašifrovaný zpráv.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="b1e2c-123">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="b1e2c-124">Tento atribut je typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1e2c-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b1e2c-125">Child Elements</span></span>  
 <span data-ttu-id="b1e2c-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="b1e2c-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1e2c-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b1e2c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b1e2c-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="b1e2c-128">Element</span></span>|<span data-ttu-id="b1e2c-129">Popis</span><span class="sxs-lookup"><span data-stu-id="b1e2c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1e2c-130">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="b1e2c-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b1e2c-131">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1e2c-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1e2c-132">Remarks</span></span>  
 <span data-ttu-id="b1e2c-133">Na základě datového proudu přenosu inovace podporují přenosy, které používají protokol orientovaný na stream jako je například TCP a pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="b1e2c-134">Konkrétně WCF poskytuje upgradů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b1e2c-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="b1e2c-135">Konfigurace tohoto zabezpečení přenosu jsou zapouzdřena objektem tento prvek konfigurace a také zobrazením [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), které se konfigurují a přidat do vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="b1e2c-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e2c-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1e2c-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="b1e2c-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="b1e2c-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b1e2c-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="b1e2c-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b1e2c-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="b1e2c-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b1e2c-140">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="b1e2c-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
