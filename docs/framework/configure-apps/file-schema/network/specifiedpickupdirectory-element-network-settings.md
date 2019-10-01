---
title: <specifiedPickupDirectory> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 47aa357dac8b6bf71ce8c391004af16f8c98e347
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697596"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="cc074-102">@no__t – element > 0specifiedPickupDirectory (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="cc074-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="cc074-103">Nakonfiguruje místní adresář pro server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="cc074-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[<span data-ttu-id="cc074-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="cc074-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="cc074-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="cc074-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="cc074-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="cc074-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>  
<span data-ttu-id="cc074-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<smtp >** ](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="cc074-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>  
<span data-ttu-id="cc074-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<specifiedPickupDirectory >**</span><span class="sxs-lookup"><span data-stu-id="cc074-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc074-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc074-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc074-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cc074-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cc074-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cc074-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc074-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="cc074-112">Attributes</span></span>  
  
|<span data-ttu-id="cc074-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="cc074-113">Attribute</span></span>|<span data-ttu-id="cc074-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cc074-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="cc074-115">Adresář, ve kterém aplikace ukládají e-mail pro pozdější zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="cc074-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc074-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cc074-116">Child Elements</span></span>  
 <span data-ttu-id="cc074-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="cc074-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc074-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cc074-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cc074-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="cc074-119">Element</span></span>|<span data-ttu-id="cc074-120">Popis</span><span class="sxs-lookup"><span data-stu-id="cc074-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc074-121">@no__t – element > 1smtp (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="cc074-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="cc074-122">Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="cc074-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc074-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc074-123">Remarks</span></span>  
 <span data-ttu-id="cc074-124">Atribut `specifiedPickupDirectory` Nastavuje adresář, ve kterém aplikace ukládají e-mailové zprávy, které server SMTP zpracuje.</span><span class="sxs-lookup"><span data-stu-id="cc074-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc074-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc074-125">Example</span></span>  
 <span data-ttu-id="cc074-126">Následující příklad určuje c:\maildrop jako předávací adresář pošty.</span><span class="sxs-lookup"><span data-stu-id="cc074-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc074-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc074-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="cc074-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="cc074-128">Network Settings Schema</span></span>](index.md)
