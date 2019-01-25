---
title: '&lt;SMTP&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 4a2947594f5adc9cc4c11471e133c6a4f2662a50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638012"
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="840d7-102">&lt;SMTP&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="840d7-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="840d7-103">Nastaví formát dodání, způsob dodání a adresu odesílatele pro zasílání e-mailů.</span><span class="sxs-lookup"><span data-stu-id="840d7-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="840d7-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="840d7-104">\<configuration></span></span>  
<span data-ttu-id="840d7-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="840d7-105">\<system.net></span></span>  
<span data-ttu-id="840d7-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="840d7-106">\<mailSettings></span></span>  
<span data-ttu-id="840d7-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="840d7-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="840d7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="840d7-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="840d7-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="840d7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="840d7-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="840d7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="840d7-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="840d7-111">Attributes</span></span>  
  
|<span data-ttu-id="840d7-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="840d7-112">Attribute</span></span>|<span data-ttu-id="840d7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="840d7-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="840d7-114">Určuje formát doručení odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="840d7-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="840d7-115">Přípustné hodnoty jsou SevenBit a mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="840d7-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="840d7-116">Určuje způsob doručení e-mailů.</span><span class="sxs-lookup"><span data-stu-id="840d7-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="840d7-117">Přípustné hodnoty jsou síť, PickupDirectoryFromIis a SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="840d7-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="840d7-118">Určuje, adresu od pro odchozí e-maily.</span><span class="sxs-lookup"><span data-stu-id="840d7-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="840d7-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="840d7-119">Child Elements</span></span>  
  
|<span data-ttu-id="840d7-120">Atribut</span><span class="sxs-lookup"><span data-stu-id="840d7-120">Attribute</span></span>|<span data-ttu-id="840d7-121">Popis</span><span class="sxs-lookup"><span data-stu-id="840d7-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="840d7-122">Konfiguruje místní adresář pro server Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="840d7-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="840d7-123">Konfiguruje možnosti sítě pro externí server SMTP.</span><span class="sxs-lookup"><span data-stu-id="840d7-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="840d7-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="840d7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="840d7-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="840d7-125">**Element**</span></span>|<span data-ttu-id="840d7-126">**Popis**</span><span class="sxs-lookup"><span data-stu-id="840d7-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="840d7-127">\<mailSettings – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="840d7-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="840d7-128">Konfiguruje možnosti pro odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="840d7-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="840d7-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="840d7-129">Example</span></span>  
 <span data-ttu-id="840d7-130">Následující příklad určuje příslušné parametry protokolu SMTP k odesílání e-mailů pomocí výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="840d7-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="840d7-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="840d7-131">See also</span></span>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="840d7-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="840d7-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
