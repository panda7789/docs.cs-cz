---
title: <smtp> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 1b5f7406f995a86f0a192dbf3249c067dff570ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140371"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="f3d39-102">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f3d39-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="f3d39-103">Nastaví formát dodání, způsob dodání a adresu odesílatele pro zasílání e-mailů.</span><span class="sxs-lookup"><span data-stu-id="f3d39-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="f3d39-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="f3d39-104">\<configuration></span></span>  
<span data-ttu-id="f3d39-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f3d39-105">\<system.net></span></span>  
<span data-ttu-id="f3d39-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="f3d39-106">\<mailSettings></span></span>  
<span data-ttu-id="f3d39-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="f3d39-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3d39-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3d39-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3d39-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3d39-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f3d39-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3d39-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3d39-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3d39-111">Attributes</span></span>  
  
|<span data-ttu-id="f3d39-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3d39-112">Attribute</span></span>|<span data-ttu-id="f3d39-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f3d39-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="f3d39-114">Určuje formát doručení odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="f3d39-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="f3d39-115">Přípustné hodnoty jsou SevenBit a mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="f3d39-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="f3d39-116">Určuje způsob doručení e-mailů.</span><span class="sxs-lookup"><span data-stu-id="f3d39-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="f3d39-117">Přípustné hodnoty jsou síť, PickupDirectoryFromIis a SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="f3d39-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="f3d39-118">Určuje, adresu od pro odchozí e-maily.</span><span class="sxs-lookup"><span data-stu-id="f3d39-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3d39-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3d39-119">Child Elements</span></span>  
  
|<span data-ttu-id="f3d39-120">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3d39-120">Attribute</span></span>|<span data-ttu-id="f3d39-121">Popis</span><span class="sxs-lookup"><span data-stu-id="f3d39-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="f3d39-122">Konfiguruje místní adresář pro server Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="f3d39-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="f3d39-123">Konfiguruje možnosti sítě pro externí server SMTP.</span><span class="sxs-lookup"><span data-stu-id="f3d39-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3d39-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3d39-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f3d39-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="f3d39-125">**Element**</span></span>|<span data-ttu-id="f3d39-126">**Popis**</span><span class="sxs-lookup"><span data-stu-id="f3d39-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f3d39-127">\<mailSettings – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f3d39-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="f3d39-128">Konfiguruje možnosti pro odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="f3d39-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f3d39-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3d39-129">Example</span></span>  
 <span data-ttu-id="f3d39-130">Následující příklad určuje příslušné parametry protokolu SMTP k odesílání e-mailů pomocí výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="f3d39-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3d39-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3d39-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="f3d39-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="f3d39-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
