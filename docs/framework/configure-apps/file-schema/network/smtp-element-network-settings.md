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
ms.openlocfilehash: 2105a6dd25a7f6e5e4c1ce286be7f60beae1dca0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697611"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="d0eb0-102">@no__t – element > 0smtp (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="d0eb0-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="d0eb0-103">Konfiguruje formát doručení, způsob doručení a adresu odesílatele pro odesílání e-mailů.</span><span class="sxs-lookup"><span data-stu-id="d0eb0-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[<span data-ttu-id="d0eb0-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="d0eb0-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="d0eb0-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d0eb0-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="d0eb0-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d0eb0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>  
<span data-ttu-id="d0eb0-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<smtp >**</span><span class="sxs-lookup"><span data-stu-id="d0eb0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0eb0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0eb0-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0eb0-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d0eb0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d0eb0-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d0eb0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0eb0-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="d0eb0-111">Attributes</span></span>  
  
|<span data-ttu-id="d0eb0-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="d0eb0-112">Attribute</span></span>|<span data-ttu-id="d0eb0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d0eb0-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="d0eb0-114">Určuje formát doručení odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="d0eb0-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="d0eb0-115">Přijatelné hodnoty jsou SevenBit a International.</span><span class="sxs-lookup"><span data-stu-id="d0eb0-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="d0eb0-116">Určuje způsob doručování e-mailů.</span><span class="sxs-lookup"><span data-stu-id="d0eb0-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="d0eb0-117">Přijatelné hodnoty jsou Network, PickupDirectoryFromIis a SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="d0eb0-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="d0eb0-118">Určuje adresu od v případě odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="d0eb0-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0eb0-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d0eb0-119">Child Elements</span></span>  
  
|<span data-ttu-id="d0eb0-120">Atribut</span><span class="sxs-lookup"><span data-stu-id="d0eb0-120">Attribute</span></span>|<span data-ttu-id="d0eb0-121">Popis</span><span class="sxs-lookup"><span data-stu-id="d0eb0-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="d0eb0-122">Nakonfiguruje místní adresář pro server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="d0eb0-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="d0eb0-123">Nakonfiguruje možnosti sítě pro externí server SMTP.</span><span class="sxs-lookup"><span data-stu-id="d0eb0-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0eb0-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d0eb0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d0eb0-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="d0eb0-125">**Element**</span></span>|<span data-ttu-id="d0eb0-126">**Popis**</span><span class="sxs-lookup"><span data-stu-id="d0eb0-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d0eb0-127">@no__t – element > 1mailSettings (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="d0eb0-127">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="d0eb0-128">Nakonfiguruje možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="d0eb0-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d0eb0-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0eb0-129">Example</span></span>  
 <span data-ttu-id="d0eb0-130">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="d0eb0-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0eb0-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0eb0-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="d0eb0-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="d0eb0-132">Network Settings Schema</span></span>](index.md)
