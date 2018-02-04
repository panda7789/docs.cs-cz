---
title: "&lt;mailSettings –&gt; – Element (nastavení sítě)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: ce7ec8bea57436ebd184cf0d593870999405f72f
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="e81cb-102">&lt;mailSettings –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e81cb-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="e81cb-103">Nakonfiguruje možnosti odesílání e-mailu.</span><span class="sxs-lookup"><span data-stu-id="e81cb-103">Configures mail sending options.</span></span>  

<span data-ttu-id="e81cb-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="e81cb-104">\<configuration></span></span>  
<span data-ttu-id="e81cb-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e81cb-105">\<system.net></span></span>  
<span data-ttu-id="e81cb-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="e81cb-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e81cb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e81cb-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e81cb-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e81cb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e81cb-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e81cb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e81cb-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e81cb-110">Attributes</span></span>  
 <span data-ttu-id="e81cb-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="e81cb-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e81cb-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e81cb-112">Child Elements</span></span>  
  
|<span data-ttu-id="e81cb-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="e81cb-113">Attribute</span></span>|<span data-ttu-id="e81cb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e81cb-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="e81cb-115">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e81cb-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="e81cb-116">Nakonfiguruje možnosti protokolu přenosu e-mailu.</span><span class="sxs-lookup"><span data-stu-id="e81cb-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e81cb-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e81cb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e81cb-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="e81cb-118">**Element**</span></span>|<span data-ttu-id="e81cb-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e81cb-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e81cb-120">\<system.Net> Element (Network Settings)</span><span class="sxs-lookup"><span data-stu-id="e81cb-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="e81cb-121">Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="e81cb-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e81cb-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="e81cb-122">Example</span></span>  
 <span data-ttu-id="e81cb-123">Následující příklad určuje vhodné parametry SMTP pro odeslání e-mailu pomocí výchozích pověření sítě.</span><span class="sxs-lookup"><span data-stu-id="e81cb-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
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
  
## <a name="see-also"></a><span data-ttu-id="e81cb-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e81cb-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="e81cb-125">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="e81cb-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
