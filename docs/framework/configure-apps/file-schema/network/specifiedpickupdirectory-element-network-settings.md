---
title: '&lt;specifiedPickupDirectory&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b62dc1a9118f7d4f1f693ade36626deaecd23999
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47459734"
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="21bf5-102">&lt;specifiedPickupDirectory&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="21bf5-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="21bf5-103">Konfiguruje místní adresář pro server Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="21bf5-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="21bf5-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="21bf5-104">\<configuration></span></span>  
<span data-ttu-id="21bf5-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="21bf5-105">\<system.net></span></span>  
<span data-ttu-id="21bf5-106">\<mailSettings – ></span><span class="sxs-lookup"><span data-stu-id="21bf5-106">\<mailSettings></span></span>  
<span data-ttu-id="21bf5-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="21bf5-107">\<smtp></span></span>  
<span data-ttu-id="21bf5-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="21bf5-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21bf5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21bf5-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21bf5-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="21bf5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="21bf5-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="21bf5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21bf5-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="21bf5-112">Attributes</span></span>  
  
|<span data-ttu-id="21bf5-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="21bf5-113">Attribute</span></span>|<span data-ttu-id="21bf5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="21bf5-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="21bf5-115">Adresář, kde aplikace ukládat e-mailu pro pozdější zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="21bf5-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21bf5-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="21bf5-116">Child Elements</span></span>  
 <span data-ttu-id="21bf5-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="21bf5-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21bf5-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="21bf5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="21bf5-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="21bf5-119">Element</span></span>|<span data-ttu-id="21bf5-120">Popis</span><span class="sxs-lookup"><span data-stu-id="21bf5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21bf5-121">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="21bf5-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="21bf5-122">Konfiguruje možnosti pro odesílání pošty Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="21bf5-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21bf5-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21bf5-123">Remarks</span></span>  
 <span data-ttu-id="21bf5-124">`specifiedPickupDirectory` Atribut nastaví adresář, kde aplikace ukládat e-mailové zprávy na zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="21bf5-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21bf5-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="21bf5-125">Example</span></span>  
 <span data-ttu-id="21bf5-126">Následující příklad určuje c:\maildrop jako předávací adresář pošty.</span><span class="sxs-lookup"><span data-stu-id="21bf5-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21bf5-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="21bf5-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="21bf5-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="21bf5-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
