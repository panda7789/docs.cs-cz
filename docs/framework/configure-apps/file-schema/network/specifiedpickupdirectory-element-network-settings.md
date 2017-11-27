---
title: "&lt;specifiedpickupdirectory –&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ffe34e6a811dd644b149a0fda12f1d1cd338c761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="1da76-102">&lt;specifiedpickupdirectory –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="1da76-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="1da76-103">Nakonfiguruje místní adresář pro přenos protokolu SMTP (Simple Mail) serveru.</span><span class="sxs-lookup"><span data-stu-id="1da76-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="1da76-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="1da76-104">\<configuration></span></span>  
<span data-ttu-id="1da76-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="1da76-105">\<system.net></span></span>  
<span data-ttu-id="1da76-106">\<mailSettings – ></span><span class="sxs-lookup"><span data-stu-id="1da76-106">\<mailSettings></span></span>  
<span data-ttu-id="1da76-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="1da76-107">\<smtp></span></span>  
<span data-ttu-id="1da76-108">\<specifiedpickupdirectory – ></span><span class="sxs-lookup"><span data-stu-id="1da76-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da76-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1da76-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1da76-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1da76-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1da76-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1da76-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1da76-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1da76-112">Attributes</span></span>  
  
|<span data-ttu-id="1da76-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1da76-113">Attribute</span></span>|<span data-ttu-id="1da76-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1da76-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="1da76-115">Adresář, kde aplikace ukládání e-mailů pro pozdější zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="1da76-115">The directory where applications save e-mail for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1da76-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1da76-116">Child Elements</span></span>  
 <span data-ttu-id="1da76-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="1da76-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1da76-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1da76-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1da76-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="1da76-119">Element</span></span>|<span data-ttu-id="1da76-120">Popis</span><span class="sxs-lookup"><span data-stu-id="1da76-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1da76-121">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="1da76-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="1da76-122">Nakonfiguruje možnosti odesílání e-mailu přenosu protokolu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="1da76-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1da76-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1da76-123">Remarks</span></span>  
 <span data-ttu-id="1da76-124">`specifiedPickupDirectory` Atribut nastaví adresář, kde aplikace uložit e-mailových zpráv, které mají být zpracovány serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="1da76-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1da76-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="1da76-125">Example</span></span>  
 <span data-ttu-id="1da76-126">Následující příklad určuje c:\maildrop jako předávací adresář pošty.</span><span class="sxs-lookup"><span data-stu-id="1da76-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="specifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1da76-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="1da76-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="1da76-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="1da76-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
