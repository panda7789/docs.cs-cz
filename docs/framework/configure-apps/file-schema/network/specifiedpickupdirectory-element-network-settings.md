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
ms.openlocfilehash: a459fee557285935c383dcfaf512c8a8a9aea570
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099271"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="fdba6-102">\<specifiedpickupdirectory – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="fdba6-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="fdba6-103">Konfiguruje místní adresář pro server Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="fdba6-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="fdba6-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fdba6-104">\<configuration></span></span>  
<span data-ttu-id="fdba6-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fdba6-105">\<system.net></span></span>  
<span data-ttu-id="fdba6-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="fdba6-106">\<mailSettings></span></span>  
<span data-ttu-id="fdba6-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="fdba6-107">\<smtp></span></span>  
<span data-ttu-id="fdba6-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="fdba6-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdba6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdba6-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdba6-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fdba6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fdba6-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fdba6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdba6-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="fdba6-112">Attributes</span></span>  
  
|<span data-ttu-id="fdba6-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="fdba6-113">Attribute</span></span>|<span data-ttu-id="fdba6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="fdba6-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="fdba6-115">Adresář, kde aplikace ukládat e-mailu pro pozdější zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="fdba6-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdba6-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fdba6-116">Child Elements</span></span>  
 <span data-ttu-id="fdba6-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="fdba6-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fdba6-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fdba6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fdba6-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="fdba6-119">Element</span></span>|<span data-ttu-id="fdba6-120">Popis</span><span class="sxs-lookup"><span data-stu-id="fdba6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdba6-121">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="fdba6-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="fdba6-122">Konfiguruje možnosti pro odesílání pošty Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="fdba6-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdba6-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdba6-123">Remarks</span></span>  
 <span data-ttu-id="fdba6-124">`specifiedPickupDirectory` Atribut nastaví adresář, kde aplikace ukládat e-mailové zprávy na zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="fdba6-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdba6-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="fdba6-125">Example</span></span>  
 <span data-ttu-id="fdba6-126">Následující příklad určuje c:\maildrop jako předávací adresář pošty.</span><span class="sxs-lookup"><span data-stu-id="fdba6-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fdba6-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdba6-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="fdba6-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="fdba6-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
