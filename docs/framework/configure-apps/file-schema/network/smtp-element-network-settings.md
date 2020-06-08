---
title: <smtp> – element (nastavení sítě)
description: <smtp>Prvek nastavení sítě konfiguruje formát doručení, způsob doručení a adresu odesílatele pro odeslání možností e-mailu v .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: b30b82922a69ea660f4c4abfd808e89fa9945183
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504508"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="77d33-103">\<smtp> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="77d33-103">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="77d33-104">Konfiguruje formát doručení, způsob doručení a adresu odesílatele pro odesílání e-mailů.</span><span class="sxs-lookup"><span data-stu-id="77d33-104">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="77d33-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77d33-105">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77d33-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="77d33-106">Attributes and Elements</span></span>  
 <span data-ttu-id="77d33-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="77d33-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77d33-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="77d33-108">Attributes</span></span>  
  
|<span data-ttu-id="77d33-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="77d33-109">Attribute</span></span>|<span data-ttu-id="77d33-110">Popis</span><span class="sxs-lookup"><span data-stu-id="77d33-110">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="77d33-111">Určuje formát doručení odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="77d33-111">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="77d33-112">Přijatelné hodnoty jsou SevenBit a International.</span><span class="sxs-lookup"><span data-stu-id="77d33-112">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="77d33-113">Určuje způsob doručování e-mailů.</span><span class="sxs-lookup"><span data-stu-id="77d33-113">Specifies the delivery method for emails.</span></span> <span data-ttu-id="77d33-114">Přijatelné hodnoty jsou Network, PickupDirectoryFromIis a SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="77d33-114">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="77d33-115">Určuje adresu od v případě odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="77d33-115">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77d33-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="77d33-116">Child Elements</span></span>  
  
|<span data-ttu-id="77d33-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="77d33-117">Attribute</span></span>|<span data-ttu-id="77d33-118">Popis</span><span class="sxs-lookup"><span data-stu-id="77d33-118">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="77d33-119">Nakonfiguruje místní adresář pro server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="77d33-119">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="77d33-120">Nakonfiguruje možnosti sítě pro externí server SMTP.</span><span class="sxs-lookup"><span data-stu-id="77d33-120">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77d33-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="77d33-121">Parent Elements</span></span>  
  
|<span data-ttu-id="77d33-122">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="77d33-122">**Element**</span></span>|<span data-ttu-id="77d33-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="77d33-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="77d33-124">\<mailSettings>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="77d33-124">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="77d33-125">Nakonfiguruje možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="77d33-125">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="77d33-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="77d33-126">Example</span></span>  
 <span data-ttu-id="77d33-127">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="77d33-127">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="77d33-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77d33-128">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="77d33-129">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="77d33-129">Network Settings Schema</span></span>](index.md)
