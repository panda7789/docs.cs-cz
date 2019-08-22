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
ms.openlocfilehash: ac9405fdc6123a5a1352de06f94fefb6d7d4014b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659125"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="eded6-102">\<> elementu SMTP (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="eded6-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="eded6-103">Konfiguruje formát doručení, způsob doručení a adresu odesílatele pro odesílání e-mailů.</span><span class="sxs-lookup"><span data-stu-id="eded6-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="eded6-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="eded6-104">\<configuration></span></span>  
<span data-ttu-id="eded6-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="eded6-105">\<system.net></span></span>  
<span data-ttu-id="eded6-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="eded6-106">\<mailSettings></span></span>  
<span data-ttu-id="eded6-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="eded6-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eded6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eded6-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eded6-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eded6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eded6-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eded6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eded6-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="eded6-111">Attributes</span></span>  
  
|<span data-ttu-id="eded6-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="eded6-112">Attribute</span></span>|<span data-ttu-id="eded6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="eded6-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="eded6-114">Určuje formát doručení odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="eded6-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="eded6-115">Přijatelné hodnoty jsou SevenBit a International.</span><span class="sxs-lookup"><span data-stu-id="eded6-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="eded6-116">Určuje způsob doručování e-mailů.</span><span class="sxs-lookup"><span data-stu-id="eded6-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="eded6-117">Přijatelné hodnoty jsou Network, PickupDirectoryFromIis a SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="eded6-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="eded6-118">Určuje adresu od v případě odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="eded6-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eded6-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eded6-119">Child Elements</span></span>  
  
|<span data-ttu-id="eded6-120">Atribut</span><span class="sxs-lookup"><span data-stu-id="eded6-120">Attribute</span></span>|<span data-ttu-id="eded6-121">Popis</span><span class="sxs-lookup"><span data-stu-id="eded6-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="eded6-122">Nakonfiguruje místní adresář pro server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="eded6-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="eded6-123">Nakonfiguruje možnosti sítě pro externí server SMTP.</span><span class="sxs-lookup"><span data-stu-id="eded6-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eded6-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eded6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="eded6-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="eded6-125">**Element**</span></span>|<span data-ttu-id="eded6-126">**Popis**</span><span class="sxs-lookup"><span data-stu-id="eded6-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eded6-127">\<mailSettings – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="eded6-127">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="eded6-128">Nakonfiguruje možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="eded6-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="eded6-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="eded6-129">Example</span></span>  
 <span data-ttu-id="eded6-130">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="eded6-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eded6-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eded6-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="eded6-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="eded6-132">Network Settings Schema</span></span>](index.md)
