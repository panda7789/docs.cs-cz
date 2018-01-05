---
title: "&lt;SMTP&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 598fe3dc2a49187e923cd689f863d0a3327e735f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="3d4d3-102">&lt;SMTP&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3d4d3-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="3d4d3-103">Nakonfiguruje formát doručení, metodu doručení a z adresy pro odesílání e-mailů.</span><span class="sxs-lookup"><span data-stu-id="3d4d3-103">Configures the delivery format, delivery method, and from address for sending e-mails.</span></span>  
  
 <span data-ttu-id="3d4d3-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="3d4d3-104">\<configuration></span></span>  
<span data-ttu-id="3d4d3-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="3d4d3-105">\<system.net></span></span>  
<span data-ttu-id="3d4d3-106">\<mailSettings – ></span><span class="sxs-lookup"><span data-stu-id="3d4d3-106">\<mailSettings></span></span>  
<span data-ttu-id="3d4d3-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="3d4d3-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d4d3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d4d3-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d4d3-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3d4d3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3d4d3-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3d4d3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d4d3-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="3d4d3-111">Attributes</span></span>  
  
|<span data-ttu-id="3d4d3-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="3d4d3-112">Attribute</span></span>|<span data-ttu-id="3d4d3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3d4d3-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="3d4d3-114">Určuje formát doručení pro odchozí e-mailů.</span><span class="sxs-lookup"><span data-stu-id="3d4d3-114">Specifies the delivery format for outgoing e-mails.</span></span> <span data-ttu-id="3d4d3-115">Přípustné hodnoty jsou SevenBit a mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="3d4d3-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="3d4d3-116">Určuje metodu doručení e-mailů.</span><span class="sxs-lookup"><span data-stu-id="3d4d3-116">Specifies the delivery method for e-mails.</span></span> <span data-ttu-id="3d4d3-117">Přípustné hodnoty jsou sítě, pickupDirectoryFromIis a specifiedpickupdirectory –.</span><span class="sxs-lookup"><span data-stu-id="3d4d3-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="3d4d3-118">Určuje z adresy pro odchozí e-mailů.</span><span class="sxs-lookup"><span data-stu-id="3d4d3-118">Specifies the from address for outgoing e-mails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d4d3-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3d4d3-119">Child Elements</span></span>  
  
|<span data-ttu-id="3d4d3-120">Atribut</span><span class="sxs-lookup"><span data-stu-id="3d4d3-120">Attribute</span></span>|<span data-ttu-id="3d4d3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="3d4d3-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="3d4d3-122">Nakonfiguruje místní adresář pro přenos protokolu SMTP (Simple Mail) serveru.</span><span class="sxs-lookup"><span data-stu-id="3d4d3-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="3d4d3-123">Nakonfiguruje možnosti sítě pro externí server SMTP.</span><span class="sxs-lookup"><span data-stu-id="3d4d3-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d4d3-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3d4d3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3d4d3-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="3d4d3-125">**Element**</span></span>|<span data-ttu-id="3d4d3-126">**Popis**</span><span class="sxs-lookup"><span data-stu-id="3d4d3-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3d4d3-127">\<mailSettings – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3d4d3-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="3d4d3-128">Nakonfiguruje možnosti odesílání e-mailu.</span><span class="sxs-lookup"><span data-stu-id="3d4d3-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3d4d3-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d4d3-129">Example</span></span>  
 <span data-ttu-id="3d4d3-130">Následující příklad určuje vhodné parametry SMTP pro odeslání e-mailu pomocí výchozích pověření sítě.</span><span class="sxs-lookup"><span data-stu-id="3d4d3-130">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
  
## <a name="see-also"></a><span data-ttu-id="3d4d3-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d4d3-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="3d4d3-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="3d4d3-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
