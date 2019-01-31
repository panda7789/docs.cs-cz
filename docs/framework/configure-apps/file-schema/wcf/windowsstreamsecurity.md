---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: aff415bb75cf719ce19fb2189cc69c2c159af6cf
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281005"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="a19ae-101">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="a19ae-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="a19ae-102">Zadejte nastavení zabezpečení datového proudu Windows pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="a19ae-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="a19ae-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a19ae-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a19ae-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a19ae-104">\<bindings></span></span>  
<span data-ttu-id="a19ae-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a19ae-105">\<customBinding></span></span>  
<span data-ttu-id="a19ae-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="a19ae-106">\<binding></span></span>  
<span data-ttu-id="a19ae-107">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="a19ae-107">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a19ae-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a19ae-108">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a19ae-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a19ae-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a19ae-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a19ae-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a19ae-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a19ae-111">Attributes</span></span>  
  
|<span data-ttu-id="a19ae-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="a19ae-112">Attribute</span></span>|<span data-ttu-id="a19ae-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a19ae-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a19ae-114">Třída protectionLevel</span><span class="sxs-lookup"><span data-stu-id="a19ae-114">protectionLevel</span></span>|<span data-ttu-id="a19ae-115">Definuje zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="a19ae-115">Defines message-level security.</span></span> <span data-ttu-id="a19ae-116">Podepisování zpráv snižuje riziko manipulace s zprávy při jejich přenosu od jiných dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="a19ae-116">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="a19ae-117">Šifrování poskytuje data úrovně ochrany osobních údajů při přenosu.</span><span class="sxs-lookup"><span data-stu-id="a19ae-117">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="a19ae-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="a19ae-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a19ae-119">-Žádný: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="a19ae-119">-   None: No protection.</span></span><br /><span data-ttu-id="a19ae-120">– Přihlášení: Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="a19ae-120">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a19ae-121">-EncryptAndSign: Zprávy jsou podepsaný a zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="a19ae-121">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="a19ae-122">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="a19ae-122">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="a19ae-123">Tento atribut je typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="a19ae-123">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a19ae-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a19ae-124">Child Elements</span></span>  
 <span data-ttu-id="a19ae-125">Žádná</span><span class="sxs-lookup"><span data-stu-id="a19ae-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a19ae-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a19ae-126">Parent Elements</span></span>  
  
|<span data-ttu-id="a19ae-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="a19ae-127">Element</span></span>|<span data-ttu-id="a19ae-128">Popis</span><span class="sxs-lookup"><span data-stu-id="a19ae-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a19ae-129">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="a19ae-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a19ae-130">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="a19ae-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a19ae-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a19ae-131">Remarks</span></span>  
 <span data-ttu-id="a19ae-132">Na základě datového proudu přenosu inovace podporují přenosy, které používají protokol orientovaný na stream jako je například TCP a pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="a19ae-132">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="a19ae-133">Konkrétně WCF poskytuje upgradů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a19ae-133">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="a19ae-134">Konfigurace tohoto zabezpečení přenosu jsou zapouzdřena objektem tento prvek konfigurace a také zobrazením [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), které se konfigurují a přidat do vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="a19ae-134">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a19ae-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a19ae-135">See also</span></span>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="a19ae-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="a19ae-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a19ae-137">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="a19ae-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a19ae-138">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="a19ae-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a19ae-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a19ae-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
